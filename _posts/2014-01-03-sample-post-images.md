---
layout: post
title: "A Post with Images"
description: "Examples and code for displaying images in posts."
category: photos
tags: [sample post, images, test]
imagefeature: picture-15.jpg
comments: true
share: true
---

Here are some examples of what a post with images might look like. If you want to display two or three images next to each other responsively use `figure` with the appropriate `class`. Images are responsive and are opened in a Magnific Popup lightbox if you link a larger image to the entry. Also if you link a larger image, the image thumbs uses CSS3 transitions to turn B&W and change back to color on mouse-hover. Each instance of `figure` is auto-numbered and displayed in the caption.

## Figures (for images or video)

### One Up

<figure>
	<a href="{{ site.url }}/gallery/disneyland.jpg"><img src="{{ site.url }}/gallery/disneyland.jpg"></a>
	<figcaption><a href="{{ site.url }}" data-toggle="tooltip" title="Visit my website">A day at Disneyland, Tokyo</a>.</figcaption>
</figure>

### Two Up

Apply the `half` class like so to display two images side by side that share the same caption.

{% highlight html %}
<figure class="half">
	<img src="/gallery/image-filename-1.jpg">
	<img src="/gallery/image-filename-2.jpg">
	<figcaption>Caption describing these two images.</figcaption>
</figure>
{% endhighlight %}

And you'll get something that looks like this:

<figure class="half">
	<a href="{{ site.url }}/gallery/photo (6).jpg"><img src="{{ site.url }}/gallery/photo (5).jpg"></a>
	<a href="{{ site.url }}/gallery/photo (12).jpg"><img src="{{ site.url }}/gallery/photo (11).jpg"></a>
	<img src="{{ site.url }}/gallery/photo (13).jpg"></a>
	<img src="{{ site.url }}/gallery/photo (19).jpg"></a>
	<figcaption>Two images.</figcaption>
</figure>

### Three Up

Apply the `third` class like so to display three images side by side that share the same caption.

{% highlight html %}
<figure class="third">
	<a href="http://placehold.it/1200x600.jpg"><img src="http://placehold.it/600x300.jpg"></a>
	<a href="http://placehold.it/1200x600.jpg"><img src="http://placehold.it/600x300.jpg"></a>
	<a href="http://placehold.it/1200x600.jpg"><img src="http://placehold.it/600x300.jpg"></a>
	<figcaption>Caption describing these three images.</figcaption>
</figure>
{% endhighlight %}

And you'll get something that looks like this:

<figure class="third">
	<a href="{{ site.url }}/gallery/photo (22).jpg"><img src="{{ site.url }}/gallery/photo (21).jpg"></a>
	<a href="{{ site.url }}/gallery/photo (24).jpg"><img src="{{ site.url }}/gallery/photo (23).jpg"></a>
	<a href="{{ site.url }}/gallery/photo (74).jpg"><img src="{{ site.url }}/gallery/photo (73).jpg"></a>
	<a href="{{ site.url }}/gallery/photo (4).jpg"><img src="{{ site.url }}/gallery/photo (3).jpg"></a>
	<a href="{{ site.url }}/gallery/photo (18).jpg"><img src="{{ site.url }}/gallery/photo (17).jpg"></a>
	<a href="{{ site.url }}/gallery/photo (10).jpg"><img src="{{ site.url }}/gallery/photo (9).jpg"></a>
	<figcaption>Three images.</figcaption>
</figure>