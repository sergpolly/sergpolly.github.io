---
layout: post
title:  "HPCC launch example"
date:   2016-12-28 1:13:43 -0500
categories: jekyll update
---

Not using HPCC often enough leads to memory washout ...

It is the right time to perpetuate some of the simple HPCC examples once and for all...

Image you have a program to run `./run` with multiple values of an input parameter 'P', than you can launch multiple independent calculation with all of required values of the parameter in parallel:


{% highlight bash %}
for P in `seq 0 1 10`; do
	bsub -n 1 -q short -W 0:30 -R "rusage[mem=1024]" -J Job\_$P ./run $P output\_$P.out
done
{% endhighlight %}


This simple snippet would launch `./run` for 11 values of `P`, from 0 to 10 including using command `bsub` (aka submit).
Each submitted instance would allocate 1 CPU (`-n 1`), 1GB of RAM (`-R "rusage[mem=1024]"`) and would be terminated after 30 min (`-W 0:30`). Each job instance would produce some log output files with the `Job\_$P` prefix and `./run` would store the results of calculations in `output\_$P.out`.

`bsub` is the submission command for the HPCC, so if the above snippet is wrapped in bash script `submit11.sh`, than all you need is to run it "locally" `sh submit11.sh`. No need to `bsub submit11.sh`!!!
We covered here one important use case scenario for the HPCC use, that would be it.




PS extra bash snippets:
nested loops for `seq` command:
{% highlight bash %}
for X in `seq 0.0 0.5 2.5`; do
	for Y in `seq 0 1e+1 1e+2`; do
		echo $X_$Y;
	done ;
done
{% endhighlight %}

and one more: concatenating multiple sequences ...
{% highlight bash %}
seq 3 1 5; seq 8 2 15
{% endhighlight %}
would generate the following sequence: `3 4 5 8 10 12 14`.


