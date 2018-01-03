# Later - aka l8r

An API that stores URLs to read, watch, listen to later on any device.

## Contributors
- [Colin Devroe](http://cdevroe.com)

## API Documentation

### Endpoint prefixes for versioning:

1. /v1/

### Methods

- `/add`              - add new URL
- `/archive`          - archive a URL
- `/delete`           - delete a URL
- `/edit`             - edit a URL's metadata
- `/list`             - list a user's URLs
- `/restore`          - unarchive a URL
- `/view`             - show a URL's metadata


### Arguments

- **id**                (int)                           - The id of the URL.
- **title (t)**         (string, required)              - The title of the link.
- **url (u)**           (string, required)              - The URL of the link.
- **source (s)**        (string, required)              - The source the URL was saved from. E.g. "Chrome on Mac" or "Via Mobile".
- **note (n)**          (string, optional)              - A note about the link. E.g. "My brother sent me this."
- **label (l)**         (string, optional)              - The Action Label E.g. "Watch"
- **tag (tg)**          (string, optional)              - Comma separated list of Tags E.g. "podcast, thewestwingweekly"
- **context (c)**       (string, optional)              - Comma separated list of Contexts E.g. "work, home"
- **sortby (srtby)**    (string, optional)              - Used to sort lists. E.g. "date"
- **sortorder (srtor)** (string, optional)              - Used to sort lists. E.g. "asc"
- **archive (ar)**                (int, optional)                 - Used to filter lists by archived. E.g. 1 = show archived URLs, 0 (default) show unarchived URLs

## Method documentation

### /add

This adds a URL to a user's list.

#### Accepts:
- title*
- url*
- source*
- note
- label
- tag
- context

#### Returns:
- `/view`

### archive

This archives a URL from the user's list. It can be restored.

#### Accepts:
- id*

#### Returns:
- `/view`

### /delete

This deletes a URL from a user's list. Cannot be undone.

#### Accepts:
- id*

#### Returns:
- true (success)
- false (fail)

### /edit

This edits the metadata on a URL. All values are overwritten with each new call. The following arguments cannot be changed once set: ID, u, s.

#### Accepts:
- id*
- title*
- note
- label
- tag
- context

#### Returns:
- `/view`

### /list

This lists a user's URL. By default, it shows the unarchived URLs.

#### Accepts:
- archive     - show archive 1, 0
- sortby      - date (default)
- sortorder   - asc (default), desc

#### Returns:
- List of URLs

### /restore

Restores a URL from the archive.

#### Accepts:
- id*

#### Returns:
- `/view`

### /view

Shows a URLs metadata.

#### Accepts:
- id*

#### Returns:
- All metadata of a URL


## Version History

- **1.0.0 Build 001** - January 3, 2018
    - Initial readme document for API scheme.