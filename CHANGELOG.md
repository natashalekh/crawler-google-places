## 2021-08-12
*Fixes*
- Fixed problem that `startUrls` was not picking up all provided URLs sometimes (due to automatic `uniqueKey` resolution)
- `likesCount` in reviews

## 2021-08-06
*Fixes*
- `maxCrawledPlaces` now compares to total sum of all places

*Features*
- Added `maxCrawledPlacesPerSearch` to limit max places per search term or search URL

## 2021-07-26
*Fixes*
- Address is now parsed correctly into components even when you supply direct place IDs

- Migrated code from `apify` 0.22.5 to 1.3.1

## 2021-07-13
- Added `county` to geolocation options

## 2021-06-03
*Fixes*
(hopefully last fixes after the layout change)
- Scraping all images per place works again 
- Fixed `additionalInfo`
- Fixed `openiningHours`

## 2021-06-03
*Fixes*
- Fix handling of search pages without results
- Skip empty searches that sometimes users accidentally post

## 2021-05-25
*Features*
- Added orderBy attribute to result scrape

## 2021-05-18
*Fixes*
- Fully or partially fixed consent screen issues
- Should also help with `Failed to set the 'innerHTML' property on 'Element': This document requires 'TrustedHTML' assignment.` which is caused by injecting JQuery into constent screen

## 2021-04-29
*Fixes*
- Fixed `reviewsTranslation`

## 2021-04-28
*Fixes after Google changed layout, not everything was fixed. Next batch of fixed asap!*
- Fixed additional data
- Fixed search pagination getting into infinite loop
- Fixed empty search handling
- Fixed reviews not being scraped
- Fixed `totalScore`

## 2021-03-22
**Warning** - Next version will be a breaking one as we will remove personal data from reviews by default. You will have to explicitly enable the fields below.
*Features*
- Added input fields to selectively pick which personal data fields to scrape - `scrapeReviewerName`, `scrapeReviewerId`, `scrapeReviewerUrl`, `scrapeReviewId`, `scrapeReviewUrl`, `scrapeResponseFromOwnerText`

## 2021-03-17
*Fixes*
- Removed duplicate reviews + all reviews scraped correctly
- `reviewsSort` finally works correctly
- Reviews scraping is now significantly faster
- Handle error that irregularly happened when scraping huge amount of reviews

*Features*
- Added `reviewsDistribution`
- Added `publishedAtDate` (exact date), `responseFromOwnerDate` and `responseFromOwnerText `for each review

## 2021-03-10
Fixes:
- `totalScore` and `reviewsCount` are now correctly extracted for all languages
- `startUrls` now correctly work non-.com domains and on detail places

## 2021-02-02
Fixes:
- Search keyword that links only to a single place (like `"London Eye"`) now works correctly

## 2021-01-27
Features:
- Address is parsed into `neighborhood`, `street`, `city`, `postalCode`, `state` and `countryCode` fields
- Added `reviewsTranslation` option to adjust how Google translates reviews from non-English languages
- Parsing ads. This means a bit more results. Those that are ads have `"isAdvertisement": true` field.
- Added `useCachedPlaces` option to load places from your KV Store. Useful if you need to scrape the same places regularly.
- Added `polygon` option to provide your own geolocation polygon.

Fixes:
- This one is big. We removed the infamous `Place is outside of required location (polygon)` error. The location of a place is now checked during paginating and these places are skipped. This means a **massive speed up of the scraper**.

## 2021-01-11
Features:
- Automatic screenshots of errors to see what went wrong
- Added `searchPageUrl` to output
- Added `PLACES-OUT-OF-POLYOGON` record to Key-Value store. You can check what places were excluded.

Fixes:
- Fixed rare bug with saving stats
- Improvement in review sorting - but it is still not ideal, more work needs to be done

## 2020-11-16
- Added postal code geolocation to input
- Improved errors when location is not found
- Optimization - Removed geolocation data from intermediate requests

## 2020-10-29
- Fixed handling of Google consent screen
- Better input validation and deprecation logs
- Changed default for `maxImages` to `1` as it doesn't require scrolling for the main image
- `imageUrls` are returned with the highest resolution

## 2020-10-27
- Removed `forceEng` input in favor of `language`

## 2020-10-15
- The default setup now uses `maxImages: 0` and `maxReviews: 0` to improve efficiency

## 2020-10-01
- added several browser options to input - `maxConcurrency`, `maxPageRetries`, `pageLoadTimeoutSec`, `maxPagesPerBrowser`, `useChrome`
- rewamped input schema and readme
- Added `reviewerNumberOfReviews` and `isLocalGuide` to reviews

## 2020-09-22
- added few extra review fields (ID, URL)

## 2020-07-23 small features
### New features
 - add an option for caching place location
 - add an option for sorting of reviews
 - add stats logging

## 2020-07 polygon search and bug fixes
### breaking change
 - reworked input search string

### Bug fixes
 - opening hour parsing (#39)
 - separate locatedIn field (#32)
 - update readme

### New features
 - extract additional info - Service Options, Highlights, Offerings,.. (#41)
 - add `maxReviews`, `maxImages` (#40)
 - add `temporarilyClosed` and `permanentlyClosed` flags (#33)
 - allow to scrape only places urls (#29)
 - add `forceEnglish` flag into input (#24, #21)
 - add searching in polygon using nominatim.org
 - add startUrls
 - added `maxAutomaticZoomOut` to limit how far can Google zoom out (it naturally zooms out as you press next page in search)

