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
<center>
	<img src="/media/unmapped_pairs.png" width="50%" align="middle"/>
</center>
 - uncompressed file with these pairs was still noth of 6GB, see `xxx.pairs`
 - but the coolest thing is that `lz4` compressed pairs file was just 85MB:
<center>
	<img src="/media/unmapped_compressed.png" width="100%" align="middle"/>
</center>
