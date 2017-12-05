<!-- ## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/Knocker4/lotr-social-graphs/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/Knocker4/lotr-social-graphs/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.


### Time to change some stuff

```python
# some comment
print "Hello there"
```

Here is a nice picture:
-->

<!-- ![Lotr Logo](https://raw.githubusercontent.com/Knocker4/lotr-social-graphs/gh-pages/images/lotr.jpeg) -->

# Introduction

The project presented resolves around the vast universe of Middle-Earth. Here we are going to explore this world from the perspective of characters. 

Since there are so many of them, it is hard to really understand how much influence particular characters had over the others. On top of that, a large portion of Tolkien's books revolve around the races and tension between them. Thus we will also look into that and try to figure out which races interact most with which, which race is the most influential one, and which is the least.

Another topic worth looking into is the long-term fandom's debate of what is better: the books or the movies. Here we will analyze sentiment of three Lord of The Rings books and compare that to the sentiment of the movies, to see if the movies actually have the same feelings in it, or are they happier, or do they lack the intensity of the feelings of the book.

Last, but not least, we will be looking into the sentiment of interactions between each of the main characters of the LoTR books. Do Aragorn and Frodo share happy memories? Do Legolas and Gimly fight more than laugh around? Did Pippin and Merry ever had sad moments at all?

# Characters network

We kick off our journey there and back again by creating the network of all the characters. In order to do that, we are going to use [The One Wiki To Rule Them All](http://lotr.wikia.com/wiki/Main_Page). 

Using their api we fetch all of the characters and the links between them and build our network. Here it is in its raw state:

> Initial graph

The number of nodes in this graph is 784, each node represents one charater and each edge represents the link between two characters. As one can notice there are quite a lot of characters with barely any links, thus they are not worth investingating into and we should clean them up. we will perform the clean up by extracting the giant connected component. This leaves us with the following graph:

> Giant component, no races

Here we are left with 752 characters. What you haven't been told yet is that together with characters and links, we fetched their races from the api. Thus each node has a 'race' item associated with it and we can use that information to assign each node its respective color:

> Network with races, with no size difference

By looking at that graph one could get an idea that humans are pretty much the most influencial race in the history, but is it really true? Lets try to shape our graph a little bit by changing the size of the node based on its degree (we don't differentiate between in and out degree here, because we are working with an undirected graph):

> Races network with sizes

Suddenly the picture has changed. Humans are still quite important all around, but look at those hobbits: they are deffinitely worth being taken to Isengard!

Based on everything descried above, here are top five races that had the biggest impact in the universe:

> Top 5 races


# Compared sentiment analysis of LoTR books and movies

In order to perform sentiment analysis we need to find the full text of movie scripts and books. Here is where we managed to find them:
<!-- We managed to find full text of books here: [The Fellowship of the Ring](http://portal.tolkienianos.pt/files/The_LotR_I.pdf), [The Two Towers](http://portal.tolkienianos.pt/files/The_LotR_II.pdf), [The Return of the King](http://portal.tolkienianos.pt/files/The_LotR_III.pdf); and the full text of movie scripts here: [FOTR](http://www.fempiror.com/otherscripts/LordoftheRings1-FOTR.pdf) , [The Two Towers](http://www.fempiror.com/otherscripts/LordoftheRings2-TTT.pdf), [The Return of the King](http://www.fempiror.com/otherscripts/LordoftheRings3-ROTK.pdf) -->

|  Volume  |  Book    |  Screenplay    |
| -------- | *------* | *------------* |
|The Fellowship of the Ring | http://portal.tolkienianos.pt/files/The_LotR_I.pdf | http://www.fempiror.com/otherscripts/LordoftheRings1-FOTR.pdf |
<!-- | The Two Towers | http://portal.tolkienianos.pt/files/The_LotR_II.pdf | http://www.fempiror.com/otherscripts/LordoftheRings2-TTT.pdf |
| The Return of the King | http://portal.tolkienianos.pt/files/The_LotR_III.pdf | http://www.fempiror.com/otherscripts/LordoftheRings3-ROTK.pdf |
 -->

# Sentiment analysis of interractions of characters

