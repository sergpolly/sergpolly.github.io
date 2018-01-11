---
layout: post
title:  "Mapping NGS data fun"
date:   2018-01-11 11:47:43 -0500
categories: jekyll update
---

Yesterday, I was doing some routine data processing, and made a "tiny" mistake along the way:
turned out I mapped mouse-NGS data to human genome hg19 (reason being - stupid "copy-paste").

Interesting consequences of such mistake:

 - only 40'000 or so read-pairs were mapped out of ~0.5 billion incoming short reads
 - resultant pairs file, thus, mostly made up of identical lines:

<!-- ![useful image](/media/unmapped_pairs.png) -->
<a href="https://sergpolly.github.io/some_image/">
  <img src="/media/unmapped_pairs.png">
</a>