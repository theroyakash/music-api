# Music API by theroyakash

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Spohisticated music search API for free. Unlimited calls for search on Apple Music and 1000 daily calls for search on YouTube.

# Make your apps with Music API
### URL
`GET https://getmusic.theroyakash.repl.co/api/{service_name}/v1?q={search_term}`.
### YouTube Search
Get the top YouTube Search result. Make you queries' words seperated by +. For example for searching Slow dance ava max you should add the quiry string as `Slow+dance+ava+max` at the end of URL. 
For example to get Past life by Selena Gomez search on YouTube, URL should look like this:
`GET https://getmusic.theroyakash.repl.co/api/youtube/v1?q=Past+life+by+selena+Gomez`
### Returns
```JSON
{
   "title":"Trevor Daniel, Selena Gomez - Past Life (Official Video)",
   "description":"Listen to \"Past Life\" by Trevor Daniel and Selena Gomez: https://smarturl.it/PastLifeOutNow Directed by Vania Heymann and Gal Muggia Produced by Iconoclast ...",
   "channelTitle":"SelenaGomezVEVO",
   "video_link":"https://www.youtube.com/watch?v=1AhOK4UwAMs",
   "thumbnail":"https://i.ytimg.com/vi/1AhOK4UwAMs/hqdefault.jpg",
   "Attribute":"API Made possible by @theroyakash"
}
```
### Apple Music Search
Get the top Apple Music Search result. Make you queries' words seperated by +. For example for searching Slow dance ava max you should add the quiry string as `Slow+dance+ava+max` at the end of URL. 
For example to get Past life by Selena Gomez search on Apple Music, URL should look like this:
`GET https://getmusic.theroyakash.repl.co/api/applemusic/v1?q=Past+life+by+selena+Gomez`
### Returns
```JSON
{
   "title":"Past Life - Single",
   "artist_name":"Trevor Daniel & Selena Gomez",
   "track_viewURL":"https://music.apple.com/us/album/past-life/1519294336?i=1519294351&uo=4",
   "image_url":"https://is2-ssl.mzstatic.com/image/thumb/Music123/v4/98/a1/48/98a14854-7844-4734-962d-f800e108c7a2/source/100x100bb.jpg",
   "short_music_preview":"https://audio-ssl.itunes.apple.com/itunes-assets/AudioPreview113/v4/73/94/3b/73943bcf-912f-8511-d34e-1c8afde3be40/mzaf_13241148759024177055.plus.aac.p.m4a",
   "Attribute":"API Made possible by @theroyakash"
}
```
## Make it work on your app
### Swift (Apple Music Example)
Use this swift code to parse the JSON as a starter. Modify it accoring to your need
```swift
// To parse the JSON, add this file to your project and do:

import Foundation
let music = try? JSONDecoder().decode(Music.self, from: jsonData)

// MARK: - Music
class Music: Codable {
    let title, musicDescription, channelTitle: String
    let videoLink: String
    let thumbnail: String
    let attribute: String

    enum CodingKeys: String, CodingKey {
        case title
        case musicDescription = "description"
        case channelTitle
        case videoLink = "video_link"
        case thumbnail
        case attribute = "Attribute"
    }

    init(title: String, musicDescription: String, channelTitle: String, videoLink: String, thumbnail: String, attribute: String) {
        self.title = title
        self.musicDescription = musicDescription
        self.channelTitle = channelTitle
        self.videoLink = videoLink
        self.thumbnail = thumbnail
        self.attribute = attribute
    }
}
```
### Python (Apple Music Example)
GET the data:
```python
import requests, json
get = requests.get('https://getmusic.theroyakash.repl.co/api/youtube/v1?q=Past+life+by+selena+Gomez').json()
```
Now use this as a boiler plate code to parse.
```python
class Music:
    title: str
    description: str
    channel_title: str
    video_link: str
    thumbnail: str
    attribute: str

    def __init__(self, title: str, description: str, channel_title: str, video_link: str, thumbnail: str, attribute: str) -> None:
        self.title = title
        self.description = description
        self.channel_title = channel_title
        self.video_link = video_link
        self.thumbnail = thumbnail
        self.attribute = attribute
```
### 


### TO-DO
- Implement a Spotify Search. (Currently working, wanna contribute?) [Contact Now](https://www.iamroyakash.com/contact)
- Maybe add Saavn.

License
----
MIT

**Free API, Hell Yeah!**
