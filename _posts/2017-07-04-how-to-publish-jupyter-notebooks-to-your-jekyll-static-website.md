---
layout: post
title: "2017 07 04 How to Publish Jupyter Notebooks to Your Jekyll Static Website"
tags:
    - python
    - notebook
--- 
This post was written in a Jupyter Notebook. Here's how I got it onto my Jekyll
website.

[Venture here](https://gist.github.com/tgarc/7d6901858ef708030c19) and download
the following GitHub gists (thanks to [cscorley](https://github.com/cscorley)
and [tgarc](https://github.com/tgarc) for putting these together): `jekyll.py`
and `jekyll.tpl`.
* I put the **`jekyll.py`** file in my GitHub pages folder (i.e.
`~/username.github.io/`). Make sure you read the comments and update the
settings where appropriate.
* The **`jekyll.tpl`** file is a template file that we'll give to Jupyter to
convert our notebook, so put it somewhere you put your Jupyter templates.

Go over to your `~/username.github.io/_posts` folder and fire up Jupyter:

```
~/username.github.io/_posts $ jupyter notebook
```

Once you're finished writing your notebook, save it, then convert it using the
jekyll.tpl template:

```
~/username.github.io/_posts $ jupyter nbconvert --to markdown
<notebook_filename>.ipynb --config ../jekyll.py
```

**Tip:** Jekyll needs your post markdown files named in a specific way in order
to pick them up to build, i.e. "YYYY-MM-DD-title-of-blogpost.md". If you name
your notebook with that in mind (e.g. "2017 07 04 How to Publish Jupyter
Notebooks to Your Jekyll Static Website"), it will automatically be in the right
file name format when you convert it. Once your finished editing just update the
title of the post in the markdown file.

**About Images:** When Jupyter converts the notebook, it saves images into a
sub-directory of the current directory (in our case, `_posts/`). Unfortunately
there is a bug in Jekyll that throws an exception if it finds a `.png` file in
the `_posts` folder ([read about the issue
here](https://github.com/jekyll/jekyll/issues/5181)). Pratically that means you
have to cut+paste the images that were saved into the `/images/` folder in the
root blog directly. If this issue gets fixed that shouldn't be a problem anymore
and the `jekyll.py` code can be updated to point to the saved images in the sub-
directory. 
 
## Example 

**In [1]:**

{% highlight python %}
# Normal Distribution
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline
{% endhighlight %}

**In [2]:**

{% highlight python %}
plt.hist(np.random.normal(size=100000), bins=30)
plt.show()
{% endhighlight %}

 
![png]({{ BASE_PATH }}/images/2017-07-04-how-to-publish-jupyter-notebooks-to-your-jekyll-static-website_3_0.png) 

