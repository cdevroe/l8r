# Later - aka l8r

An API that stores URLs to read, watch, listen to later on any device.

## Contributors
- [Colin Devroe](http://cdevroe.com)

## API Documentation

### Endpoint prefixes for versioning:

1. `/v1/`

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
- **tags (tg)**          (string, optional)              - Comma separated list of Tags E.g. "podcast, thewestwingweekly"
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
- tags
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
- tags
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

##### Example JSON Response

```json
{
    "list": [
        {
            "id": 1,
            "title": "Colin Devroe &#8211; Reverse Engineer. Blogger.",
            "url": "http://cdevroe.com/",
            "source": "iOS Share Extension",
            "archived": 0,
            "note": "One of the best blogs evar.",
            "label": "Read",
            "tags": [
                {
                    "id": 1,
                    "label": "blog",
                    "dateAdded": "12-01-2017"
                },
                {
                    "id": 2,
                    "label": "personal",
                    "dateAdded": "12-04-2017"
                },
                {
                    "id": 3,
                    "label": "micro-blog",
                    "dateAdded": "12-04-2017"
                }
            ],
            "context": "Home"
        },
        {
            "id": 2,
            "title": "Internet Archive: Digital Library of Free Books, Movies, Music & Wayback Machine",
            "url": "http://archive.org/",
            "source": "Chrome Extension",
            "archived": 1,
            "note": "",
            "label": "Read",
            "tags": [
                {
                    "id": 4,
                    "label": "internet",
                    "dateAdded": "12-01-2017"
                },
                {
                    "id": 5,
                    "label": "history",
                    "dateAdded": "12-04-2017"
                },
                {
                    "id": 6,
                    "label": "non-profit",
                    "dateAdded": "12-04-2017"
                }
            ],
            "context": "Work"
        },
    ]
}
```

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

##### Example JSON response

```json
{
    "id": 1,
    "title": "Colin Devroe &#8211; Reverse Engineer. Blogger.",
    "url": "http://cdevroe.com/",
    "archived": 0,
    "source": "iOS Share Extension",
    "note": "One of the best blogs evar.",
    "label": "Read",
    "tags": [
      {
         "id": 1,
         "label": "blog",
         "dateAdded": "12-01-2017"
      },
      {
         "id": 2,
         "label": "personal",
         "dateAdded": "12-04-2017"
      },
      {
         "id": 3,
         "label": "micro-blog",
         "dateAdded": "12-04-2017"
      }
   ],
    "context": "Home"
}
```


## Version History

- **1.0.0 Build 001** - January 3, 2018
    - Initial readme document for API scheme.