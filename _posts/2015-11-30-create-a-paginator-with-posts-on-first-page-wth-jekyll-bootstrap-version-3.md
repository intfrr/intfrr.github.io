---
layout: post
title: "Create a paginator with posts on first page with jekyll bootstrap version 3"
description: "Learning to create a paginator with posts on first page with jekyll bootstrap version 3"
category: personal
tags: [[tutorial]]
---
{% include JB/setup %}
This article describes how to create a paginator with posts on first page with jekyll bootstrap version 3

# Overview

## What is Jekyll Boostrap 3

The quickest way to start and publish your Jekyll powered blog. 100% compatible with GitHub pages version 3

## What is a pagination

Pagination is the process of dividing a document into discrete pages, either electronic pages or printed pages. Today printed pages are usually produced by outputting an electronic file to a printing device, such as a desktop printer or a modern printing press. These electronic files may for example be Microsoft Word, PDF or QXD files. They will usually already incorporate the instructions for pagination, among other formatting instructions. Pagination encompasses rules and algorithms for deciding where page breaks will fall, which depend partly on cultural considerations about which content belongs on the same page: for example one may try to avoid widows and orphans. Some systems are more sophisticated than others in this respect. Before the rise of information technology (IT), pagination was a manual process: all pagination was decided by a human. Today, most pagination is performed by machines, although humans often override particular decisions (e.g. by inserting a hard page break).


### Examples


<a href="https://intfrr.github.io">https://intfrr.github.io</a>


# How to make this happen

According to

<a href="http://jekyllrb.com/docs/pagination/">http://jekyllrb.com/docs/pagination/</a>

And

<a href="https://gist.github.com/nimbupani/1421828">https://gist.github.com/nimbupani/1421828</a>

And

<a href="https://gist.github.com/intfrr/0c3956ceb4e2e59cdd21">https://gist.github.com/intfrr/0c3956ceb4e2e59cdd21</a>


## Setup

On _config.yml

	paginate: 1
	paginate_path: "posts/page:num/"

### Install and configuration

Put this on index.html

<a href="https://gist.github.com/intfrr/0c3956ceb4e2e59cdd21">https://gist.github.com/intfrr/0c3956ceb4e2e59cdd21</a>


	{{ "{% include JB/setup " }}%}

	<div class="blog-index">
		{{ "{% assign post = site.posts.first " }}%}
		{{ "{% assign content = post.content " }}%}
	</div>


	<!--
		This loops through the paginated posts
		And renders the post
	-->
	{{ "{% assign i = 0 " }}%}
	{{ "{% for post in paginator.posts " }}%}

		{{ "{% if i == 0 " }}%}
			<h1><a href="{{ "{{ post.url " }}}}">{{ "{{ post.title " }}}}</a></h1>
			<p class="author">
				<span class="date">{{ "{{ post.date | date: '%B %d, %Y' " }}}}</span>
			</p>
			<div class="content">
				{{ "{{ post.content " }}}}
			</div>
		{{ "{% endif " }}%}
		{{ "{% assign i = i | plus: 1 " }}%}
	{{ "{% endfor " }}%}

	<hr/>

	<!--
		This loops through the paginated posts
		And get the actual post's index
	-->
	{{ "{% assign next_post_index = 1 " }}%}
	{{ "{% for page in (1..paginator.total_pages) " }}%}
		{{ "{% if page == paginator.page " }}%}
			{{ "{% break " }}%}
		{{ "{% endif " }}%}
		{{ "{% assign next_post_index = next_post_index | plus: 1 " }}%}
	{{ "{% endfor " }}%}

	<!--
		This loops through the paginated posts
		And renders the next post
	-->
	{{ "{% assign next_post_index = next_post_index | plus: 1 " }}%}
	<!--<h1>{{next_post_index}}</h1>-->

	{{ "{% assign i = 1 " }}%}
	{{ "{% for post in site.posts " }}%}
		{{ "{% if i == next_post_index" }}%}
			{{ "{% if post.hidden != true " }}%}

				<article class="home" style="margin-top:40px">

					<span class="post-date">
						{{ "{% assign d = post.date | date: "%d" | plus:'0' " }}%}
						{{ "{{ post.date | date: "%B" " }}}}
						{{ "{% case d " }}%}
						{{ "{% when 1 or 21 or 31 " }}%}{{ d }}st,
						{{ "{% when 2 or 22 " }}%}{{ d }}nd,
						{{ "{% when 3 or 23 " }}%}{{ d }}rd,
						{{ "{% else " }}%}{{ d }}th,
						{{ "{% endcase " }}%}
						{{ "{{ post.date | date: "%Y" " }}}}
					</span>

					<h3>

						<a href="{{ "{{ BASE_PATH " }}}}{{ "{{ post.url " }}}}">{{ "{{post.title " }}}}</a>
					</h3>

					<div>

						{{ "{% if post.fullview " }}%}

							{{ "{{ post.content " }}}}
						{{ "{% else " }}%}

							<a href="{{ "{{ BASE_PATH }}{{ "{{post.url }}">
								{{ "{% if post.shortinfo " }}%}
									{{ "{{ post.shortinfo " }}}}
								{{ "{% elsif post.description " }}%}
									{{ "{{ post.description " }}}}
								{{ "{% else " }}%}
									{{ "{{ post.excerpt " }}}}
								{{ "{% endif " }}%}
							</a>
						{{ "{% endif " }}%}
					</div>

				</article>
			{{ "{% endif " }}%}
		{{ "{% endif " }}%}
		{{ "{% assign i = i | plus: 1 " }}%}
	{{ "{% endfor " }}%}

	<hr/>

	<!--
		This loops through the paginated posts
		And renders the pager
	-->
	<ul class="pager">

		{{ "{% if paginator.previous_page " }}%}
		<li class="previous">
			{{ "{% if paginator.previous_page == 1 " }}%}
			<a href="{{ "{{ BASE_PATH " }}}}/">&larr; Newer</a>
			{{ "{% else " }}%}
			<a href="{{ "{{ BASE_PATH " }}}}/{{ "{{ site.paginate_path | replace: ':num', paginator.previous_page " }}}}">&larr; Newer</a>
			{{ "{% endif " }}%}
		</li>
		{{ "{% else " }}%}
		<li class="previous disabled">
			<a>&larr; Newer</a>
		</li>
		{{ "{% endif " }}%}

		<li>
			<span class="page_number">Page: {{ "{{ paginator.page }} of {{ "{{ paginator.total_pages }}</span>
		</li>

		{{ "{% if paginator.next_page " }}%}
		<li class="next">
			<a href="{{ "{{ BASE_PATH " }}}}/{{ "{{ site.paginate_path|replace: ':num',paginator.next_page " }}}}">Older &rarr;</a>
		</li>
		{{ "{% else " }}%}
		<li class="next disabled">
			<a>Older &rarr;</a>
		</li>
		{{ "{% endif " }}%}
	</ul>



### Testing

	$ jekyll build --watch
	$ jekyll serve --safe


## Conclusion
Jekyll is great for static content

```Don't forget to change yout BASE_PATH configuration on _config.yml to push```


## Authors:
Nadir Palacios

<a href="https://gist.github.com/intfrr/0c3956ceb4e2e59cdd21">https://gist.github.com/intfrr/0c3956ceb4e2e59cdd21</a>


The jekyll team

<a href="http://jekyllrb.com/docs/pagination/">http://jekyllrb.com/docs/pagination/</a>

Divya Manian

<a href="https://gist.github.com/nimbupani/1421828">https://gist.github.com/nimbupani/1421828</a>
