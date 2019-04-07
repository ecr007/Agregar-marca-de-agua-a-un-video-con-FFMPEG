# Agregar-marca-de-agua-a-un-video-con-FFMPEG


<article id="post-500" class="post-500 post type-post status-publish format-standard has-post-thumbnail hentry category-guides tag-ffmpeg tag-video">
	<header class="entry-header">
		<h1 class="entry-title">Watermarking Videos from the Command Line with FFMPEG Filters</h1>
		<div class="entry-meta">
			<span class="posted-on">Posted on <a href="http://ksloan.net/watermarking-videos-from-the-command-line-using-ffmpeg-filters/" rel="bookmark"><time class="entry-date published" datetime="2014-10-23T23:40:00+00:00">October 23, 2014</time><time class="updated hide" datetime="2014-10-24T04:48:01+00:00">October 24, 2014</time></a></span><span class="byline"> by <span class="author vcard"><a class="url fn n" href="http://ksloan.net/author/kevin/">Kevin Sloan</a></span></span>		</div><!-- .entry-meta -->
	</header><!-- .entry-header -->

	<div class="entry-content">
		<p><a href="https://www.ffmpeg.org/ffmpeg-filters.html">FFMPEG filters</a> provide a powerful way to programmatically enhance or alter videos, and it’s fairly simple&nbsp;to add a watermark to a video using the overlay filter.&nbsp;The easiest way to install ffmpeg is to <a href="https://www.ffmpeg.org/download.html">download</a> a pre-built binary for your specific platform. Then you don’t have to worry about including and installing all the right dependencies and codecs you will be using.</p>
<p>Here’s a short video I took while mountain biking that we’ll be working with.<br>
<span id="more-500"></span></p>
<p><!--more--></p>
<p></p><center><br>
<div style="width: 480px;" class="wp-video"><!--[if lt IE 9]><script>document.createElement('video');</script><![endif]-->
<span class="mejs-offscreen">Video Player</span><div id="mep_0" class="mejs-container mejs-container-keyboard-inactive wp-video-shortcode mejs-video" tabindex="0" role="application" aria-label="Video Player" style="width: 480px; height: 270px; min-width: 217px;"><div class="mejs-inner"><div class="mejs-mediaelement"><mediaelementwrapper id="video-500-1"><video class="wp-video-shortcode" id="video-500-1_html5" width="480" height="270" preload="metadata" src="http://ksloan.net/wp-content/uploads/2014/10/birds.mp4?_=1" style="width: 480px; height: 270px;"><source type="video/mp4" src="http://ksloan.net/wp-content/uploads/2014/10/birds.mp4?_=1"><a href="http://ksloan.net/wp-content/uploads/2014/10/birds.mp4">http://ksloan.net/wp-content/uploads/2014/10/birds.mp4</a></video></mediaelementwrapper></div><div class="mejs-layers"><div class="mejs-poster mejs-layer" style="display: none; width: 100%; height: 100%;"></div><div class="mejs-overlay mejs-layer" style="width: 100%; height: 100%; display: none;"><div class="mejs-overlay-loading"><span class="mejs-overlay-loading-bg-img"></span></div></div><div class="mejs-overlay mejs-layer" style="display: none; width: 100%; height: 100%;"><div class="mejs-overlay-error"></div></div><div class="mejs-overlay mejs-layer mejs-overlay-play" style="width: 100%; height: 100%;"><div class="mejs-overlay-button" role="button" tabindex="0" aria-label="Play" aria-pressed="false"></div></div></div><div class="mejs-controls"><div class="mejs-button mejs-playpause-button mejs-play"><button type="button" aria-controls="mep_0" title="Play" aria-label="Play" tabindex="0"></button></div><div class="mejs-time mejs-currenttime-container" role="timer" aria-live="off"><span class="mejs-currenttime">00:00</span></div><div class="mejs-time-rail"><span class="mejs-time-total mejs-time-slider" role="slider" tabindex="0" aria-label="Time Slider" aria-valuemin="0" aria-valuemax="NaN" aria-valuenow="0" aria-valuetext="00:00"><span class="mejs-time-buffering" style="display: none;"></span><span class="mejs-time-loaded"></span><span class="mejs-time-current" style="transform: scaleX(0);"></span><span class="mejs-time-hovered no-hover"></span><span class="mejs-time-handle" style="transform: translateX(0px);"><span class="mejs-time-handle-content"></span></span><span class="mejs-time-float"><span class="mejs-time-float-current">00:00</span><span class="mejs-time-float-corner"></span></span></span></div><div class="mejs-time mejs-duration-container"><span class="mejs-duration">00:05</span></div><div class="mejs-button mejs-volume-button mejs-mute"><button type="button" aria-controls="mep_0" title="Mute" aria-label="Mute" tabindex="0"></button><a href="javascript:void(0);" class="mejs-volume-slider" aria-label="Volume Slider" aria-valuemin="0" aria-valuemax="100" role="slider" aria-orientation="vertical" aria-valuenow="80" aria-valuetext="80%"><span class="mejs-offscreen">Use Up/Down Arrow keys to increase or decrease volume.</span><div class="mejs-volume-total"><div class="mejs-volume-current" style="bottom: 0px; height: 80%;"></div><div class="mejs-volume-handle" style="bottom: 80%; margin-bottom: -3px;"></div></div></a></div><div class="mejs-button mejs-fullscreen-button"><button type="button" aria-controls="mep_0" title="Fullscreen" aria-label="Fullscreen" tabindex="0"></button></div></div></div></div></div><br>
</center><p></p>
<p>Once you have ffmpeg installed, adding a watermark is as easy as passing your existing source through an overlay filter like so:</p>
<pre>ffmpeg -i birds.mp4 -i watermark.png -filter_complex "overlay=10:10" birds1.mp4</pre>
<p>Basically, we’re passing in the original video, and an overlay image as inputs, then passing it through the filter, and saving the output as&nbsp;birds1.mp4.</p>
<p>We specify a specific position of the overlay in pixels – <strong>10:10</strong> puts the video 10 pixels from the top and 10 pixels from the right. (x:y coordinates)</p>
<p>Here is our result:<br>
</p><center><br>
<div style="width: 480px;" class="wp-video"><span class="mejs-offscreen">Video Player</span><div id="mep_1" class="mejs-container mejs-container-keyboard-inactive wp-video-shortcode mejs-video" tabindex="0" role="application" aria-label="Video Player" style="width: 480px; height: 270px; min-width: 217px;"><div class="mejs-inner"><div class="mejs-mediaelement"><mediaelementwrapper id="video-500-2"><video class="wp-video-shortcode" id="video-500-2_html5" width="480" height="270" preload="metadata" src="http://ksloan.net/wp-content/uploads/2014/10/birds1.mp4?_=2" style="width: 480px; height: 270px;"><source type="video/mp4" src="http://ksloan.net/wp-content/uploads/2014/10/birds1.mp4?_=2"><a href="http://ksloan.net/wp-content/uploads/2014/10/birds1.mp4">http://ksloan.net/wp-content/uploads/2014/10/birds1.mp4</a></video></mediaelementwrapper></div><div class="mejs-layers"><div class="mejs-poster mejs-layer" style="display: none; width: 100%; height: 100%;"></div><div class="mejs-overlay mejs-layer" style="width: 100%; height: 100%; display: none;"><div class="mejs-overlay-loading"><span class="mejs-overlay-loading-bg-img"></span></div></div><div class="mejs-overlay mejs-layer" style="display: none; width: 100%; height: 100%;"><div class="mejs-overlay-error"></div></div><div class="mejs-overlay mejs-layer mejs-overlay-play" style="width: 100%; height: 100%;"><div class="mejs-overlay-button" role="button" tabindex="0" aria-label="Play" aria-pressed="false"></div></div></div><div class="mejs-controls"><div class="mejs-button mejs-playpause-button mejs-play"><button type="button" aria-controls="mep_1" title="Play" aria-label="Play" tabindex="0"></button></div><div class="mejs-time mejs-currenttime-container" role="timer" aria-live="off"><span class="mejs-currenttime">00:00</span></div><div class="mejs-time-rail"><span class="mejs-time-total mejs-time-slider" role="slider" tabindex="0" aria-label="Time Slider" aria-valuemin="0" aria-valuemax="NaN" aria-valuenow="0" aria-valuetext="00:00"><span class="mejs-time-buffering" style="display: none;"></span><span class="mejs-time-loaded"></span><span class="mejs-time-current" style="transform: scaleX(0);"></span><span class="mejs-time-hovered no-hover"></span><span class="mejs-time-handle" style="transform: translateX(0px);"><span class="mejs-time-handle-content"></span></span><span class="mejs-time-float"><span class="mejs-time-float-current">00:00</span><span class="mejs-time-float-corner"></span></span></span></div><div class="mejs-time mejs-duration-container"><span class="mejs-duration">00:05</span></div><div class="mejs-button mejs-volume-button mejs-mute"><button type="button" aria-controls="mep_1" title="Mute" aria-label="Mute" tabindex="0"></button><a href="javascript:void(0);" class="mejs-volume-slider" aria-label="Volume Slider" aria-valuemin="0" aria-valuemax="100" role="slider" aria-orientation="vertical" aria-valuenow="80" aria-valuetext="80%"><span class="mejs-offscreen">Use Up/Down Arrow keys to increase or decrease volume.</span><div class="mejs-volume-total"><div class="mejs-volume-current" style="bottom: 0px; height: 80%;"></div><div class="mejs-volume-handle" style="bottom: 80%; margin-bottom: -3px;"></div></div></a></div><div class="mejs-button mejs-fullscreen-button"><button type="button" aria-controls="mep_1" title="Fullscreen" aria-label="Fullscreen" tabindex="0"></button></div></div></div></div></div><br>
</center><p></p>
<p>In some cases you might not know the exact dimensions of the videos you’ll be watermarking. Fortunately, there are variables you can use to better position your watermark depending on the size of the video. These variables include:</p>
<ul>
<li><strong>main_h</strong> – the video’s height</li>
<li><strong>main_w</strong> – the video’s width</li>
<li><strong>overlay_h</strong> – the overlay’s height</li>
<li><strong>overlay_w</strong> – the overlay’s width</li>
</ul>
<p>Using these variable we can&nbsp;position the watermark right in the center of the video like so:</p>
<pre>ffmpeg -i birds.mp4 -i watermark.png \
-filter_complex "overlay=x=(main_w-overlay_w)/2:y=(main_h-overlay_h)/2" birds2.mp4</pre>
<p></p><center><br>
<div style="width: 480px;" class="wp-video"><span class="mejs-offscreen">Video Player</span><div id="mep_2" class="mejs-container mejs-container-keyboard-inactive wp-video-shortcode mejs-video" tabindex="0" role="application" aria-label="Video Player" style="width: 480px; height: 270px; min-width: 217px;"><div class="mejs-inner"><div class="mejs-mediaelement"><mediaelementwrapper id="video-500-3"><video class="wp-video-shortcode" id="video-500-3_html5" width="480" height="270" preload="metadata" src="http://ksloan.net/wp-content/uploads/2014/10/birds2.mp4?_=3" style="width: 480px; height: 270px;"><source type="video/mp4" src="http://ksloan.net/wp-content/uploads/2014/10/birds2.mp4?_=3"><a href="http://ksloan.net/wp-content/uploads/2014/10/birds2.mp4">http://ksloan.net/wp-content/uploads/2014/10/birds2.mp4</a></video></mediaelementwrapper></div><div class="mejs-layers"><div class="mejs-poster mejs-layer" style="display: none; width: 100%; height: 100%;"></div><div class="mejs-overlay mejs-layer" style="width: 100%; height: 100%; display: none;"><div class="mejs-overlay-loading"><span class="mejs-overlay-loading-bg-img"></span></div></div><div class="mejs-overlay mejs-layer" style="display: none; width: 100%; height: 100%;"><div class="mejs-overlay-error"></div></div><div class="mejs-overlay mejs-layer mejs-overlay-play" style="width: 100%; height: 100%;"><div class="mejs-overlay-button" role="button" tabindex="0" aria-label="Play" aria-pressed="false"></div></div></div><div class="mejs-controls"><div class="mejs-button mejs-playpause-button mejs-play"><button type="button" aria-controls="mep_2" title="Play" aria-label="Play" tabindex="0"></button></div><div class="mejs-time mejs-currenttime-container" role="timer" aria-live="off"><span class="mejs-currenttime">00:00</span></div><div class="mejs-time-rail"><span class="mejs-time-total mejs-time-slider" role="slider" tabindex="0" aria-label="Time Slider" aria-valuemin="0" aria-valuemax="NaN" aria-valuenow="0" aria-valuetext="00:00"><span class="mejs-time-buffering" style="display: none;"></span><span class="mejs-time-loaded"></span><span class="mejs-time-current" style="transform: scaleX(0);"></span><span class="mejs-time-hovered no-hover"></span><span class="mejs-time-handle" style="transform: translateX(0px);"><span class="mejs-time-handle-content"></span></span><span class="mejs-time-float"><span class="mejs-time-float-current">00:00</span><span class="mejs-time-float-corner"></span></span></span></div><div class="mejs-time mejs-duration-container"><span class="mejs-duration">00:05</span></div><div class="mejs-button mejs-volume-button mejs-mute"><button type="button" aria-controls="mep_2" title="Mute" aria-label="Mute" tabindex="0"></button><a href="javascript:void(0);" class="mejs-volume-slider" aria-label="Volume Slider" aria-valuemin="0" aria-valuemax="100" role="slider" aria-orientation="vertical" aria-valuenow="80" aria-valuetext="80%"><span class="mejs-offscreen">Use Up/Down Arrow keys to increase or decrease volume.</span><div class="mejs-volume-total"><div class="mejs-volume-current" style="bottom: 0px; height: 80%;"></div><div class="mejs-volume-handle" style="bottom: 80%; margin-bottom: -3px;"></div></div></a></div><div class="mejs-button mejs-fullscreen-button"><button type="button" aria-controls="mep_2" title="Fullscreen" aria-label="Fullscreen" tabindex="0"></button></div></div></div></div></div><br>
</center><p></p>
<p>If we wanted to add branding or a watermark to the clip but not cover the existing video, we can use the <a href="https://www.ffmpeg.org/ffmpeg-filters.html#pad">pad filter</a> to add some padding to our clip, and then position our watermark over the padding like so:</p>
<pre>ffmpeg -i birds.mp4 -i watermark2.png \
-filter_complex "pad=height=ih+40:color=#71cbf4,overlay=(main_w-overlay_w)/2:main_h-overlay_h" \
birds3.mp4</pre>
<p></p><center><br>
<div style="width: 480px;" class="wp-video"><span class="mejs-offscreen">Video Player</span><div id="mep_3" class="mejs-container mejs-container-keyboard-inactive wp-video-shortcode mejs-video" tabindex="0" role="application" aria-label="Video Player" style="width: 480px; height: 294px; min-width: 217px;"><div class="mejs-inner"><div class="mejs-mediaelement"><mediaelementwrapper id="video-500-4"><video class="wp-video-shortcode" id="video-500-4_html5" width="480" height="294" preload="metadata" src="http://ksloan.net/wp-content/uploads/2014/10/birds3.mp4?_=4" style="width: 480px; height: 294px;"><source type="video/mp4" src="http://ksloan.net/wp-content/uploads/2014/10/birds3.mp4?_=4"><a href="http://ksloan.net/wp-content/uploads/2014/10/birds3.mp4">http://ksloan.net/wp-content/uploads/2014/10/birds3.mp4</a></video></mediaelementwrapper></div><div class="mejs-layers"><div class="mejs-poster mejs-layer" style="display: none; width: 100%; height: 100%;"></div><div class="mejs-overlay mejs-layer" style="width: 100%; height: 100%; display: none;"><div class="mejs-overlay-loading"><span class="mejs-overlay-loading-bg-img"></span></div></div><div class="mejs-overlay mejs-layer" style="display: none; width: 100%; height: 100%;"><div class="mejs-overlay-error"></div></div><div class="mejs-overlay mejs-layer mejs-overlay-play" style="width: 100%; height: 100%;"><div class="mejs-overlay-button" role="button" tabindex="0" aria-label="Play" aria-pressed="false"></div></div></div><div class="mejs-controls"><div class="mejs-button mejs-playpause-button mejs-play"><button type="button" aria-controls="mep_3" title="Play" aria-label="Play" tabindex="0"></button></div><div class="mejs-time mejs-currenttime-container" role="timer" aria-live="off"><span class="mejs-currenttime">00:00</span></div><div class="mejs-time-rail"><span class="mejs-time-total mejs-time-slider" role="slider" tabindex="0" aria-label="Time Slider" aria-valuemin="0" aria-valuemax="NaN" aria-valuenow="0" aria-valuetext="00:00"><span class="mejs-time-buffering" style="display: none;"></span><span class="mejs-time-loaded"></span><span class="mejs-time-current" style="transform: scaleX(0);"></span><span class="mejs-time-hovered no-hover"></span><span class="mejs-time-handle" style="transform: translateX(0px);"><span class="mejs-time-handle-content"></span></span><span class="mejs-time-float"><span class="mejs-time-float-current">00:00</span><span class="mejs-time-float-corner"></span></span></span></div><div class="mejs-time mejs-duration-container"><span class="mejs-duration">00:05</span></div><div class="mejs-button mejs-volume-button mejs-mute"><button type="button" aria-controls="mep_3" title="Mute" aria-label="Mute" tabindex="0"></button><a href="javascript:void(0);" class="mejs-volume-slider" aria-label="Volume Slider" aria-valuemin="0" aria-valuemax="100" role="slider" aria-orientation="vertical" aria-valuenow="80" aria-valuetext="80%"><span class="mejs-offscreen">Use Up/Down Arrow keys to increase or decrease volume.</span><div class="mejs-volume-total"><div class="mejs-volume-current" style="bottom: 0px; height: 80%;"></div><div class="mejs-volume-handle" style="bottom: 80%; margin-bottom: -3px;"></div></div></a></div><div class="mejs-button mejs-fullscreen-button"><button type="button" aria-controls="mep_3" title="Fullscreen" aria-label="Fullscreen" tabindex="0"></button></div></div></div></div></div><br>
</center><p></p>
<p>Once you start getting the hang of this, you can even animate your overlays!</p>
<pre>ffmpeg -i birds.mp4 -i watermark.png \
-filter_complex "overlay='if(gte(t,1), -w+(t-1)*200, NAN)':(main_h-overlay_h)/2" birds4.mp4</pre>
<p></p><center><br>
<div style="width: 480px;" class="wp-video"><span class="mejs-offscreen">Video Player</span><div id="mep_4" class="mejs-container mejs-container-keyboard-inactive wp-video-shortcode mejs-video" tabindex="0" role="application" aria-label="Video Player" style="width: 480px; height: 270px; min-width: 217px;"><div class="mejs-inner"><div class="mejs-mediaelement"><mediaelementwrapper id="video-500-5"><video class="wp-video-shortcode" id="video-500-5_html5" width="480" height="270" preload="metadata" src="http://ksloan.net/wp-content/uploads/2014/10/birds4.mp4?_=5" style="width: 480px; height: 270px;"><source type="video/mp4" src="http://ksloan.net/wp-content/uploads/2014/10/birds4.mp4?_=5"><a href="http://ksloan.net/wp-content/uploads/2014/10/birds4.mp4">http://ksloan.net/wp-content/uploads/2014/10/birds4.mp4</a></video></mediaelementwrapper></div><div class="mejs-layers"><div class="mejs-poster mejs-layer" style="display: none; width: 100%; height: 100%;"></div><div class="mejs-overlay mejs-layer" style="width: 100%; height: 100%; display: none;"><div class="mejs-overlay-loading"><span class="mejs-overlay-loading-bg-img"></span></div></div><div class="mejs-overlay mejs-layer" style="display: none; width: 100%; height: 100%;"><div class="mejs-overlay-error"></div></div><div class="mejs-overlay mejs-layer mejs-overlay-play" style="width: 100%; height: 100%;"><div class="mejs-overlay-button" role="button" tabindex="0" aria-label="Play" aria-pressed="false"></div></div></div><div class="mejs-controls"><div class="mejs-button mejs-playpause-button mejs-play"><button type="button" aria-controls="mep_4" title="Play" aria-label="Play" tabindex="0"></button></div><div class="mejs-time mejs-currenttime-container" role="timer" aria-live="off"><span class="mejs-currenttime">00:00</span></div><div class="mejs-time-rail"><span class="mejs-time-total mejs-time-slider" role="slider" tabindex="0" aria-label="Time Slider" aria-valuemin="0" aria-valuemax="NaN" aria-valuenow="0" aria-valuetext="00:00"><span class="mejs-time-buffering" style="display: none;"></span><span class="mejs-time-loaded"></span><span class="mejs-time-current" style="transform: scaleX(0);"></span><span class="mejs-time-hovered no-hover" pos="0" style="left: 0px; transform: scaleX(0);"></span><span class="mejs-time-handle" style="transform: translateX(0px);"><span class="mejs-time-handle-content"></span></span><span class="mejs-time-float" style="display: none; left: 0px;"><span class="mejs-time-float-current">00:00</span><span class="mejs-time-float-corner"></span></span></span></div><div class="mejs-time mejs-duration-container"><span class="mejs-duration">00:05</span></div><div class="mejs-button mejs-volume-button mejs-mute"><button type="button" aria-controls="mep_4" title="Mute" aria-label="Mute" tabindex="0"></button><a href="javascript:void(0);" class="mejs-volume-slider" aria-label="Volume Slider" aria-valuemin="0" aria-valuemax="100" role="slider" aria-orientation="vertical" aria-valuenow="80" aria-valuetext="80%"><span class="mejs-offscreen">Use Up/Down Arrow keys to increase or decrease volume.</span><div class="mejs-volume-total"><div class="mejs-volume-current" style="bottom: 0px; height: 80%;"></div><div class="mejs-volume-handle" style="bottom: 80%; margin-bottom: -3px;"></div></div></a></div><div class="mejs-button mejs-fullscreen-button"><button type="button" aria-controls="mep_4" title="Fullscreen" aria-label="Fullscreen" tabindex="0"></button></div></div></div></div></div><br>
</center><p></p>
<p>That’s it! Simple. Please leave comments below if you have any questions!</p>
<div class="sharedaddy sd-sharing-enabled"><div class="robots-nocontent sd-block sd-social sd-social-icon sd-sharing"><h3 class="sd-title">Share this:</h3><div class="sd-content"><ul><li class="share-twitter"><a rel="nofollow noopener noreferrer" data-shared="sharing-twitter-500" class="share-twitter sd-button share-icon no-text" href="http://ksloan.net/watermarking-videos-from-the-command-line-using-ffmpeg-filters/?share=twitter" target="_blank" title="Click to share on Twitter"><span></span><span class="sharing-screen-reader-text">Click to share on Twitter (Opens in new window)</span></a></li><li class="share-facebook"><a rel="nofollow noopener noreferrer" data-shared="sharing-facebook-500" class="share-facebook sd-button share-icon no-text" href="http://ksloan.net/watermarking-videos-from-the-command-line-using-ffmpeg-filters/?share=facebook" target="_blank" title="Click to share on Facebook"><span></span><span class="sharing-screen-reader-text">Click to share on Facebook (Opens in new window)</span></a></li><li class="share-google-plus-1"><a rel="nofollow noopener noreferrer" data-shared="sharing-google-500" class="share-google-plus-1 sd-button share-icon no-text" href="http://ksloan.net/watermarking-videos-from-the-command-line-using-ffmpeg-filters/?share=google-plus-1" target="_blank" title="Click to share on Google+"><span></span><span class="sharing-screen-reader-text">Click to share on Google+ (Opens in new window)</span></a></li><li class="share-linkedin"><a rel="nofollow noopener noreferrer" data-shared="sharing-linkedin-500" class="share-linkedin sd-button share-icon no-text" href="http://ksloan.net/watermarking-videos-from-the-command-line-using-ffmpeg-filters/?share=linkedin" target="_blank" title="Click to share on LinkedIn"><span></span><span class="sharing-screen-reader-text">Click to share on LinkedIn (Opens in new window)</span></a></li><li class="share-reddit"><a rel="nofollow noopener noreferrer" data-shared="" class="share-reddit sd-button share-icon no-text" href="http://ksloan.net/watermarking-videos-from-the-command-line-using-ffmpeg-filters/?share=reddit" target="_blank" title="Click to share on Reddit"><span></span><span class="sharing-screen-reader-text">Click to share on Reddit (Opens in new window)</span></a></li><li class="share-email"><a rel="nofollow noopener noreferrer" data-shared="" class="share-email sd-button share-icon no-text" href="http://ksloan.net/watermarking-videos-from-the-command-line-using-ffmpeg-filters/?share=email" target="_blank" title="Click to email this to a friend"><span></span><span class="sharing-screen-reader-text">Click to email this to a friend (Opens in new window)</span></a></li><li class="share-end"></li></ul></div></div></div>			</div><!-- .entry-content -->

	
</article>
