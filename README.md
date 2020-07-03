# housematching

## Idea
A recommendation system which finds property to rent or buy.

## Use case
1. User specifies filters (hard, soft, search query, free form).
2. Matching houses are shown to the user.
3. User can decline or save the option.
4. Iterations 2-3 are repeated several times until user decides to contact the property or says some options are perfect.

## Main metric
1. Number of deals.

## Operational metrics
1. Time to achieve N matches.
2. Number of saved options.
3. Time spent on the platform.
4. Number of houses on the platform.

## House properties
1. Type.
2. Pictures.
3. Amenities.
4. Floor plan.
5. Time to points of interest, commute types.
6. Local area (shops, pubs, schools, culture, beach, etc.).
7. Safety, ecology, health.
8. Free form description.
9. Price, mortgage parameters.
10. Local taxes.
11. Geo position, region.

## Data collection
Interaction with proposed options:
 - order of views
 - tabs opened
 - mouse movements within the tabs to determine the focus
 - declines and saves
 - contact information of the landlord/agency

## Filters
 - budget (cash, total, mortgage deposit/payment)
 - beds/WC/lounges with areas
 - type, ownership type, built/in_progress
 - garage/garden
 - floors
 - geo position and/or commute time to a set of POIs
 - storage needs
 - free form search query
 - upward/downward chain

## Features to use
User:
 - filters/preferences
 - demography
 - car existence/size
 - family structure
 - needs in storage/garage
 - current place of living, history

Houses:
 - type (house/flat/terraced/etc)
 - ownership type (freehold/share/lease)
 - numerical/countable values (floor area, bedrooms, room areas, WC, living rooms, parking places, garden)
 - picture embeddings
 - floor plan embeddings
 - description embeddings
 - commute to POIs structure/time/stability
 - local area features (presence/distance/quality of shops, pubs, schools)
 - safety/health/ecology
 - price and mortgage parameters
 - local taxes
 - market stats (price above/below, rent stats/opportunities.demand)

Interactions:
 - absolute and conditional (by category) likes/dislikes/view_times
 - focus on tabs/pictures
 - user embeddings (to capture personal preferences)
 - house embeddings (to capture specific properties of the house)
 - shares of the options

## Models
1. baseline: matrix decomposition (embeddings of users and houses, predict likes/dislikes)
2. linear regression: P(like/dislike | user, house, interaction features), linear combination of the features
3. neural network: P(like/dislike | user, house, interaction features), MLP
4. E(user, interactions) * E(house) -> like/dislike

In the case 4 we decompose the task on user and houses embeddings so we can quickly choose a wide range of candidates. This list can be ranked by model from point 3.

## Things to consider
 - misleading options (report incorrect info, appeals)
 - ability to contact sellers, organise meetings, help to drive to the property, virtual/online tours
 - track progress of the deal (convenient personal accounts for buyers and sellers)
 - mortgage applications
 - help to manage the property (partner with suppliers/agencies)
 - help to let the property
