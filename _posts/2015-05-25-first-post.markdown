---
layout: post
title:  "first post"
date:   2015-05-25 11:18:39
categories: jekyll update
---
first post with Jekyll

{% highlight rust %}
fn quick_sort(&mut self) {
	let length = self.len();
	if length < 2 { return; }

	let pivot_idx = self.partition();

	self[0..pivot_idx].quick_sort();
	self[pivot_idx+1..length].quick_sort();
}
{% endhighlight %}