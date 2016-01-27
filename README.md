Features
==
<li> OkHttpDataSource
<li> Subtitles (.srt files)


API
==
```CinemanaVideoPlayer  cinemanaVideoPlayer = new CinemanaVideoPlayer(this, playerFL, videoFile);```


where:
<li> **playerFL**: A `FrameLayout` to be usesd as the container of the video player.
<li> **videoFile**: A data structure that has a `HashMap` containing a resolution and its url link.
arTranslationFilePath is the url link of the subtitle as an `srt` format.

The *VideoFile* data structure is shown below:

```
    public static int QUALITY_720P = 3;
    public static int QUALITY_480P = 2;
    public static int QUALITY_360P = 1;
    public static int QUALITY_240P = 0;

    public static final int DASH = 0;
    public static final int SS = 1;
    public static final int HLS = 2;
    public static final int OTHER = 3;  // MP4 or WebM


    public int videoType = OTHER;

    public String title;
    public HashMap<Integer, String> resolutions = new HashMap<>();  // <quality, url>; e.g, <QUALITY_720P, "http://example.com/video720p.mp4"
    public int selectedResolutioin;

    public String arTranslationFilePath;
```


Subtitles
==

The subtitles style can be configured from the library in the file `CinemanaVideoPlayer.java`:

```
    private void configureSubtitleView() {
        int defaultSubtitleColor = Color.argb(255, 218, 218, 218);
        int outlineColor = Color.argb(255, 43, 43, 43);
        Typeface subtitleTypeface = Typeface.createFromAsset(surfaceView.getContext().getAssets(), "fonts/Abdo-Line.otf");
        CaptionStyleCompat style =
                new CaptionStyleCompat(defaultSubtitleColor,
                        Color.TRANSPARENT, Color.TRANSPARENT,
                        CaptionStyleCompat.EDGE_TYPE_OUTLINE,
                        outlineColor, subtitleTypeface);
        float fontScale = 2.0f;
//        if (Util.SDK_INT >= 19) {
////            style = getUserCaptionStyleV19();
//            fontScale = getUserCaptionFontScaleV19();
//        } else {
////            style = CaptionStyleCompat.DEFAULT;
//            fontScale = 1.5f;
//        }
        subtitleLayout.setStyle(style);
        subtitleLayout.setFractionalTextSize(SubtitleLayout.DEFAULT_TEXT_SIZE_FRACTION * fontScale);
    }
```


Screenshots
==
Here, it is showin an Arabic subtitle of srt type, from the Titanic movie:
<p align="center">
<img src="titanic_screenshot01.png" alt="Arabic subtitle ExoPlayer" title="Arabic subtitle ExoPlayer" width="500"/>
</p>
<p align="center">
<img src="titanic_screenshot02.png" alt="Arabic subtitle ExoPlayer" title="Arabic subtitle ExoPlayer" width="500"/>
</p>
<p align="center">
<img src="titanic_screenshot03.png" alt="Arabic subtitle ExoPlayer" title="Arabic subtitle ExoPlayer" width="500"/>
</p>
<p align="center">
<img src="titanic_screenshot04.png" alt="Arabic subtitle ExoPlayer" title="Arabic subtitle ExoPlayer" width="500"/>
</p>




Notes
==
This project was a fork from [ExoPlayerWrapper](https://github.com/cklar/ExoPlayerWrapper). Thanks a lot :)