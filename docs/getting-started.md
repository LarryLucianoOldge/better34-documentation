# Getting Started

## Prerequisite

Before you dive in, there are some requirements you need to have for utilizing 90% of the API features

1. user_id
2. api_key

In order to get both, you're required to have a Rule 34 account

**If you don't have one:** [Sign up](https://rule34.xxx/index.php?page=account&s=reg) for a new account

**If you already have one:**

* [Log in](https://rule34.xxx/index.php?page=account&s=login&code=00) to your account
* Go to [account options](https://rule34.xxx/index.php?page=account&s=options)
* Look for the "API Access Credentials". From there you could get your **user_id** and **api_key**.
* It is recommended to generate your own **api_key** by checking "Generate New Key" checkbox. What it does is they will give you your own **api_key**
!!! danger "Warning"

    Please do not spam save with "Generate New Key" option checked as R34 would flag you and your account might be suspended or limited from making api request.

* Click save
* Copy the **user_id** and the **api_key** from the "API Access Credentials" row text box. Paste it somewhere safe (in a notepad or something else). Your required credentials would look like this:
  <textarea rows="2" cols="50">&api_key=your_api-key&user_id=your_user_id</textarea>

## You're Set Up!

Let's make our first request to the site. here we are using `GET` method 

=== "URL"

    ```bash title="GET"
    https://api.rule34.xxx/index.php?page=dapi&s=post&q=index&id=15449154&api_key=your_api-key&user_id=your_user_id

    ```
=== "Bash"

    ```bash title="GET"
    curl "https://api.rule34.xxx/index.php?page=dapi&s=post&q=index&id=15449154&api_key=your_api-key&user_id=your_user_id"

    ```

```xml title="Example response"
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
  />
</posts>
```

Here you are requesting to list posts that has the `id=15449154`. Remember to add your **api_key** and **user_id** as the URL query, otherwise it will return an error response

```xml title="Error response"
<error>
  Missing authentication. Go to api.rule34.xxx for more information
</error>
```

The URL can be a little bit overwhelming with all the query parameters. If you are unfamiliar with the notation, you might want to look up URL [query string](https://en.wikipedia.org/wiki/Query_string) notation. For details of the queries and other features please refer to the [Features](features.md) page