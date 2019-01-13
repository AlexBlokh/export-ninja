# Ninja Copy Export API

### Authorization and Usage
Each request has to contain an `?:access_token` query param. To obtain `access_token` - contact me on t.me/alexblokh
Each request has a `usage` amount for your items balance.

### List of available methods
* [Get profile media feed](#profile-feed)
* [Export Instagram post comments](#export-comments)

#### Profile feed
GET /feed/:username?:limit  
`:username` - username of the instagram user. For **@nusr_et** it's going to be **nusr_et**  
`usage = 100`
```
{
  result:{
    userId,
    fullName,
    username,
    feed:[
      {
        shortCode,
        src,
        type
      }
    ]
  },
  time,
  usage
}
```

#### Export comments
GET /comments?:shortCode  
`:shortCode` - instagram post shortcode from url. For https://www.instagram.com/p/BsgvW3NFXj5/ - it's going to be **BsgvW3NFXj5**  
`usage=numComments + 50*(video/sidecar post count)`

```
  result:{
    display_url,
    type,
    caption,
    unix_time,
    date,
    sidecar:[
      {
          type,
          code,
          source,
          thumbnail
      }
    ],
    comments_count,
    comments:[
      {
        text,
        username,
        time
      }
    ],
    time,
    usage
  }
```
