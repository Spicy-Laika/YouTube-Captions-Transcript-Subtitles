# YouTube Captions Transcript Subtitles
Download &amp; convert captions in various popular formats and translate them to any language

1. **Universal Subtitle Translation 🌍**  
Translate subtitles into any language—*even those not available on YouTube*. 

2. **Download All Subtitles in One Click 📥**  
Download all available subtitles for a video instantly, saving time and effort. 

3. **Supports Multiple Subtitle Formats 🎬**  
Our service supports a variety of subtitle formats (e.g., SRT, VTT, XML, JSON), allowing you to download and use subtitles in the format that best suits your needs. 

### Response Structure `/get-video-info/{videoId}`
Paramter "format" can be `xml` or `json`, default is `json`

- **`title`** _(string)_: The title of the video.
- **`description`** _(string)_: The description of the video.
- **`author`** _(string)_: The author or the name of the channel that uploaded the video.
- **`lengthSeconds`** _(string)_: The video duration in seconds.
- **`viewCount`** _(string)_: The number of views.
- **`keywords`** _(array of strings)_: A list of keywords associated with the video.
- **`isLiveContent`** _(boolean)_: Indicates if the video is live content.
- **`thumbnail`** _(array of objects)_: A list of thumbnail images with the following properties:
  - **`url`** _(string)_: The URL of the thumbnail image.
  - **`width`** _(integer)_: The width of the thumbnail image.
  - **`height`** _(integer)_: The height of the thumbnail image.
- **`embed`** _(object)_: Embedding details for the video:
  - **`iframeUrl`** _(string)_: The URL for embedding the video.
  - **`width`** _(integer)_: The width of the embedded player.
  - **`height`** _(integer)_: The height of the embedded player.
- **`ownerProfileUrl`** _(string)_: URL to the channel's profile.
- **`externalChannelId`** _(string)_: External YouTube channel ID.
- **`isFamilySafe`** _(boolean)_: Indicates if the video is family safe.
- **`availableCountries`** _(array of strings)_: List of country codes where the video is available.
- **`isUnlisted`** _(boolean)_: Indicates if the video is unlisted.
- **`hasYpcMetadata`** _(boolean)_: Indicates if the video has YPC (YouTube Partner Content) metadata.
- **`category`** _(string)_: The category of the video (e.g., "Education").
- **`publishDate`** _(string)_: The date and time when the video was published.
- **`ownerChannelName`** _(string)_: The name of the channel that owns the video.
- **`liveBroadcastDetails`** _(object)_: Details of the live broadcast (if applicable):
  - **`isLiveNow`** _(boolean)_: Indicates if the broadcast is live.
  - **`startTimestamp`** _(string)_: The timestamp when the broadcast started.
  - **`endTimestamp`** _(string)_: The timestamp when the broadcast ended.

---

### Response Structure `/language-list/{videoId}`
Paramter "format" can be `xml` or `json`, default is `json`
- **`name`** _(string)_: The name of the available language (e.g., "Russian (auto-generated)").
- **`languageCode`** _(string)_: The language code for the available language (e.g., "ru").
- **`auto-generated`** _(integer)_: Indicates whether the language is auto-generated (1 if true, 0 if false).

---

### Response Structure `download section`
Methods:
`/download-srt/{videoId}`
`/download-xml/{videoId}`
`/download-json/{videoId}`
`/download-webvtt/{videoId}`

**Has parameter:**

`language` example `en`, It should be equal to the server response from the list of languages ​​available for video obtained by the method `/language-list/{videoId}`

**Return:** 

Subtitle in format `srt`, `xml`, `json`, `webvtt` 

**Structure for XML/JSON:**
- **`start`** _(string)_: The start time of the subtitle in seconds.
- **`dur`** _(string)_: The duration of the subtitle in seconds.
- **`text`** _(string)_: The subtitle text.

**Example:**
```
[ { "start": "0.519", "dur": "1.311", "text": "(brooding music)" }, 
{ "start": "1.83", "dur": "2.37", "text": "- [Narrator] On the\nmorning of May 5th, 2021," }, 
{ "start": "4.2", "dur": "3.87", "text": "Steven Hendrickson was driving\nhis Tesla Model 3 to work." }]
```
**Structure for SRT/WEBVTT:**

Complies with the standards of these formats

---

### Response Structure `/download-all/{videoId}`
The service's killer feature allows you to download all subtitles available for download in all available languages ​for video.

**Parameters:**

`format_subtitle` - Subtitle format `xml` `json` `srt` `webvtt` (default `json`) 


`format_answer`- Server response format `xml` or `json` (default `json`)

**Format answer**
```
array(
    "lang" =&gt; array (
            array("start" =&gt; time, "dur" =&gt; time, "text" =&gt; "text"),
            array("start" =&gt; time, "dur" =&gt; time, "text" =&gt; "text")
    )
)
```

**Example:**
```

[{
    "languageCode": "ar",
    "subtitle": [
        {
                "start": "21.05",
                "dur": "4.86",
                "text": "في الفيديو السابق لدينا ناقشنا كيف واجه الرومان ضده وتمكنوا من الهزيمة"
        },
        {
                "start": "25.91",
                "dur": "6.7",
                "text": "جيش المرتزقة في قرطاج ، وفي هذا الفيديو ، سنواصل النظر إلى أعداء روما."
        },
        {
                "start": "32.61",
                "dur": "5.25",
                "text": "في أعقاب هزيمة هانيبال في زاما ، تحولت روما انتباهها إلى Antigonid"
        }
    ]
},{
    "languageCode": "zh-CN",
    "subtitle": [
        {
                "start": "21.05",
                "dur": "4.86",
                "text": "在我们之前的视频中我们讨论了 罗马人如何面对并设法击败迦太基的雇佣军"
        },
        {
                "start": "25.91",
                "dur": "6.7",
                "text": "在这个视频中， 我们将继续关注罗马的敌人。"
        },
        {
                "start": "32.61",
                "dur": "5.25",
                "text": "在汉尼拔在扎马失利之后，"
        }]
},{
    "languageCode": "en",
    "subtitle": [
        {
                "start": "7.18",
                "dur": "6.8",
                "text": "[Music]"
        },
        {
                "start": "20.96",
                "dur": "4.239",
                "text": "in our previous video we discussed how"
        },
        {
                "start": "22.96",
                "dur": "3.12",
                "text": "the romans faced off against and managed"
        }]
}]

```
---

### **Feel free to write to me with any questions not listed in the documentation! :)**

If you have any inquiries or need further assistance, don’t hesitate to reach out. I’m here to help!


#### **Telegram Support:**

You can easily reach me on Telegram group for quick support or any additional questions.

https://t.me/+Zlto9kxqYjthYTQy

