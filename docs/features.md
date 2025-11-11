# Features

## Posts

### `[List]` Retrieve list of posts that matches your queries

**Base URL:**
`https://api.rule34.xxx/index.php?page=dapi&s=post&q=index`

| Query | Description |
| ----- | ----------- |
| limit `int` | How many posts you want to retrieve (max: 1000 post/request) |
| pid `int` | The page number |
| tags `string` | The tags to search for. Any tag combination that works on the web site will work here. This includes all the meta-tags. See [cheatsheet](https://rule34.xxx/index.php?page=help&topic=cheatsheet) for more information. |
| cid `int` | ID for changes made in the post. This is in Unix time so there are likely others with the same value if updated at the same time. |
| id `int` | The post ID |
| json `int` | Set to 1 for JSON formatted response. |

**Use Case: Retrieve a Post with a Certain ID**

=== "URL"

    ```bash title="GET"
    https://api.rule34.xxx/index.php?page=dapi&s=post&q=index&id=15449154&api_key=your_api-key&user_id=your_user_id

    ```
=== "Bash"

    ```bash title="GET"
    curl "https://api.rule34.xxx/index.php?page=dapi&s=post&q=index&id=15449154&api_key=your_api-key&user_id=your_user_id"

    ```

Responses:

=== "XML"

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <posts count="1" offset="0">
      <post 
        height="2877" 
        score="10" 
        file_url="https://api-cdn.rule34.xxx/images/..." 
        parent_id="" 
        sample_url="https://api-cdn.rule34.xxx/samples/..." 
        sample_width="850" sample_height="1140" preview_url="https://api-cdn.rule34.xxx/thumbnails/..." 
        rating="q" 
        tags="artist_name kamiya_maneki pink_eyes pink_hair shorts ..." 
        id="15449154" 
        width="2146" 
        change="1762877632" 
        md5="fd122db5648bcf8f7aff31178f4aa2a4" 
        creator_id="5296398" 
        has_children="false" 
        created_at="Tue Nov 11 17:13:52 +0100 2025" 
        status="active" 
        source="https://scrollx.org/..." 
        has_notes="false" 
        has_comments="true" 
        preview_width="111" 
        preview_height="150"
      >
      </post>
    </posts>

    ```
=== "JSON"

    ```json
    [
      {
        "preview_url": "https://api-cdn.rule34.xxx/thumbnails/...",
        "sample_url": "https://api-cdn.rule34.xxx/samples/...",
        "file_url": "https://api-cdn.rule34.xxx/images/...",
        "directory": 1516,
        "hash": "fd122db5648bcf8f7aff31178f4aa2a4",
        "width": 2146,
        "height": 2877,
        "id": 15449154,
        "image": "fd122db5...a4.jpeg",
        "change": 1762877632,
        "owner": "wowow239048",
        "parent_id": 0,
        "rating": "questionable",
        "sample": true,
        "sample_height": 1140,
        "sample_width": 850,
        "score": 13,
        "tags": "artist_name kamiya_maneki pink_eyes pink_hair ...",
        "source": "https://scrollx.org/...",
        "status": "active",
        "has_notes": false,
        "comment_count": 3
      }
    ]

    ```
=== "Error"

    ```xml
    <error>
      Missing authentication. Go to api.rule34.xxx for more information
    </error>

    ```

**Use Case: Retrieve 10 Posts with a Specifig Tag**

=== "URL"

    ```bash title="GET"
    https://api.rule34.xxx/index.php?page=dapi&s=post&q=index&tags=vaporeon&limit=10&api_key=your_api-key&user_id=your_user_id

    ```
=== "Bash"

    ```bash title="GET"
    curl "https://api.rule34.xxx/index.php?page=dapi&s=post&q=index&tags=vaporeon&limit=10&api_key=your_api-key&user_id=your_user_id"

    ```

Responses:

=== "XML"

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <posts count="15799" offset="0">
      <post height=.../>
      <post height=.../>
      <post height=.../>
      <post height=.../>
      <post height=.../>
      <post height=.../>
      <post height=.../>
      <post height=.../>
      <post height=.../>
      <post height=.../>
    </posts>

    ```
=== "JSON"

    ```json
    [
      { "preview_url": "https:"...},
      { "preview_url": "https:"...},
      { "preview_url": "https:"...},
      { "preview_url": "https:"...},
      { "preview_url": "https:"...},
      { "preview_url": "https:"...},
      { "preview_url": "https:"...},
      { "preview_url": "https:"...},
      { "preview_url": "https:"...},
      { "preview_url": "https:"...}
    ]

    ```
=== "Error"

    ```xml
    <error>
      Missing authentication. Go to api.rule34.xxx for more information
    </error>

    ```
### `[Deleted Images]` Retrieve deleted posts ID 

**Base URL:**
`https://api.rule34.xxx/index.php?page=dapi&s=post&q=index&deleted=show`

| Query | Description |
| ----- | ----------- |
| last_id `int` | A numerical value. Will return everything above this number |

**Use Case: Retrieve Posts That Got Deleted Since Post ID 1812570**

=== "URL"

    ```bash title="GET"
    https://api.rule34.xxx/index.php?page=dapi&s=post&q=index&deleted=show&last_id=1812570&api_key=your_api_key&user_id=your_user_id

    ```
=== "Bash"

    ```bash title="GET"
    curl "https://api.rule34.xxx/index.php?page=dapi&s=post&q=index&deleted=show&last_id=1812570&api_key=your_api_key&user_id=your_user_id"

    ```

Responses:

=== "XML"

    ```xml
    <posts>
      <post deleted="1812571" md5="0b77608943a1e4efd765479df6d0c81c"/>
      <post deleted="1812572" md5="50ccb0425c6ad4ac35d4ee24a3f3beec"/>
      <post deleted="1812573" md5="5fbf7b192b2dc36778fcfdbe34e3db6a"/>
      <post deleted="1812574" md5="025a99fa25e0b83347f7120438f34672"/>
      ...
      <post deleted="1812716" md5="f01817fe935a93f4b38254f678f1f88b"/>
    </posts>

    ```

=== "Error"

    ```xml
    <error>
      Missing authentication. Go to api.rule34.xxx for more information
    </error>

    ```

## Comments

### `List` Retrieve List of Comments from Specific ID

**Base URL:**
`https://api.rule34.xxx/index.php?page=dapi&s=comment&q=index`

| Query | Description |
| ----- | ----------- |
| post_id `int` | The id number of the comment to retrieve. |

**Use Case: Let's Get The Comments from The First Post Ever!**

=== "URL"

    ```bash title="GET"
    https://api.rule34.xxx/index.php?page=dapi&s=comment&q=index&post_id=1&api_key=your_api_key&user_id=your_user_id

    ```
=== "Bash"

    ```bash title="GET"
    curl "https://api.rule34.xxx/index.php?page=dapi&s=comment&q=index&post_id=1&api_key=your_api_key&user_id=your_user_id"

    ```

Responses:

=== "XML"

    ```xml
    <comments type="array">
      <comment 
        created_at="2025-11-11 20:44" 
        post_id="1" 
        body="Ground zero of Rule 34 right here, ladies, gentlemen, and whatever the hell else you choose to identify as. " 
        creator="XXXXXX" 
        id="32437034" 
        creator_id="XXXXXX"
      />
      <comment created_at="2025-11-11 20:44" .../>
      <comment created_at="2025-11-11 20:44" .../>
      <comment created_at="2025-11-11 20:44" .../>
      ...
      <comment created_at="2025-11-11 20:43" .../>
    </comments>
    ```

=== "Error"

    ```xml
    <error>
      Missing authentication. Go to api.rule34.xxx for more information
    </error>

    ```

## Tags

### `List` Retrieve List of Tags or Retrieve Specific Tags from Given Tag ID

**Base URL:**
`https://api.rule34.xxx/index.php?page=dapi&s=tag&q=index`

| Query | Description |
| ----- | ----------- |
| id `int` | The tag's ID in the database. This is useful to grab a specific tag if you already know this value. |
| limit `int` | How many tags you want to retrieve. Default: 100/ request. |
| pid* `int` | Page ID. If the limit is set to default, putting pid=1 will query the next 100 tags  |

\* not stated in the official docs

**Use Case: Retrieve The information for Tag ID 67**

=== "URL"

    ```bash title="GET"
    https://api.rule34.xxx/index.php?page=dapi&s=tag&q=index&id=67&api_key=your_api_key&user_id=your_user_id

    ```
=== "Bash"

    ```bash title="GET"
    curl "https://api.rule34.xxx/index.php?page=dapi&s=tag&q=index&id=67&api_key=your_api_key&user_id=your_user_id"

    ```

Responses:

=== "XML"

    ```xml
    <tags type="array">
      <tag 
        type="5" 
        count="710356" 
        name="uncensored" 
        ambiguous="false" 
        id="67"
      />
    </tags>
    ```

=== "Error"

    ```xml
    <error>
      Missing authentication. Go to api.rule34.xxx for more information
    </error>

    ```

## Autocomplete

### `List` Retrieve List of Tags or Retrieve Specific Tags from Given Tag ID

**Base URL:**
`https://api.rule34.xxx/autocomplete.php?q=`

| Query | Description |
| ----- | ----------- |
| q `string` | Enter any letter or incomplete tag. Not an official endpoint, but some people seem to rip the one from the main site. Use this one instead. |

**Use Case: I'm Feeling Blue, Let Me Search for Something Related to Blue**

=== "URL"

    ```bash title="GET"
    https://api.rule34.xxx/autocomplete.php?q=blue

    ```
=== "Bash"

    ```bash title="GET"
    curl "https://api.rule34.xxx/autocomplete.php?q=blue"

    ```

Responses:

=== "JSON"

    ```json
    [
      {
        "label": "blue_eyes (1490595)",
        "value": "blue_eyes"
      },
      {
        "label": "blue_hair (628767)",
        "value": "blue_hair"
      },
      ...
      {
        "label": "blue_sky (44642)",
        "value": "blue_sky"
      },
    ]
    ```