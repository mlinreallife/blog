---
title: "Doing web without JavaScript, HTML nor CSS for data science"
date: 2020-09-18T17:01:10+02:00
draft: false
---

I've recently played with a tool named *Streamlit*. I wanted to share this experience with you.
 
If you want to build a simple web page to expose your models using only Python, this library is for you.

*Streamlit* was launched the first of october in 2019. You can get more information in the [launch blog post](https://towardsdatascience.com/coding-ml-tools-like-you-code-ml-models-ddba3357eace).

Here is the traditional *hello world*:

```python
import streamlit as st

st.write("Hello world!")

```

With that, you get this:

![Hello world with Streamlit](/streamlit.png) 

To dive deeper in this tool, I recommend the [official website](https://www.streamlit.io/).

My goal with this article is telling you the benefits and disadvantages I found after using it.


## Benefits:

- Useful when you want to build a simple page quickly.
- Interesting when you want to expose a simple prediction.
- With *Streamlit*, there's no need to know HTML, CSS, etc. You only have to know Python.
- Many graphs to represent data.
- A large and active community.

This tool is built for data scientists and data science. It is helpful for simple pages, demo pages and simple predictions.
 
## Disadvantages:
- As always, these kinds of tools are not very flexible. This is not the purpose though.
- For instance, it's difficult to get different forms in one page. You can find your way with *checkboxes* instead of *submit* button. But it's a bit weird.
- It's also difficult to get different pages in one application. The option *st.cache* can save your life. But it's not enough to get a complete application.
 
## Conclusion

*Streamlit* was designed for data applications. It's not a perfect tool but a very promising one in my opinion.
