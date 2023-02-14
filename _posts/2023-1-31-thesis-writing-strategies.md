---
title: "A strategy to efficiently write your scientific thesis"
excerpt_separator: "<!--more-->"
categories:
  - Blog
tags:
  - academic writing
  - Latex
  - writing strategies
---

<!--section: Introduction st 3 pr 2 -->
In the novel *Untold Night and Day* by Bae Suah, the manager of a museum relays his experience attending a poet's convention to the young museum administrator: 

“When I first saw them [the poets], I was struck by how old, how grey, how bleak they seemed, almost without exception. It was so pronounced that at first I felt shocked. It wasn’t just abstract, it was a physical sensation coming from their bodies, as though they were emitting particles. When they gathered in the lecture hall even the lights seemed to lose their radiance, becoming dull, making the room gloomy. I don’t actually recall whether they were especially old, biologically speaking. What I do remember is their faded grey hair, their bent, almost hunched backs, their listlessly bowed necks, the glinting spectacles shielding their myopic eyes, their fatigue-inflamed irises, the harsh scent of cheap fabric, fake leather bags, facial muscles stiffened into a mask of long-suppressed frustration and sadness [...]”

<!-- Commiseration st 3 pr 2-->
Now, it's open to interpretation exactly why Bae Suah depicted the poets in this way, but I added this quote as commiseration to all those who are, at this moment, hacking out their thesis or any other writing piece. Here's to you. Writing often feels so, well, as a friend put it, crappy, that you may be able to relate to the poets at this convention. My own two cents is that writing demands a tremendous cognitive strain, and our reptile brains can find little motivation for this task and would much rather be doing something involving snacks. We know writing can involve snacks but that is beyond the scope of this work.

<!-- What's the problem segway? st 3 pr 3 -->
Now that we've commiserated, allow me to explain the strategy which I used while writing my MSc and Ph.D. theses. Actually, before that, why did I need a strategy - i.e. what are the problems when writing a thesis or essay?

## Interlocking Problems <!--section: Description of problem st 3 pr 1 -->

<!--Non-terminating writing Intro: Long parse & edit times, Excessive checking for completion, writing fluff before meat, Culminates in frustration st 3 pr 1-->
I found the most devilish problem is that writing can become a non-terminating process. As one writes, one generates more content, this needs to be constantly re-read in order to check for various things. Firstly, to check if it's complete  within itself as a section of writing with no mistakes in grammar, logic, referencing, etc. Secondly, to check how a given paragraph fits into the flow of the larger section. Thirdly, to check if the points raised in that section or paragraph link correctly to other points in other sections. Lastly, to remind yourself what that section or paragraph is actually about. As time goes on, increasingly more time is spent re-reading text. What I realized is that most of this re-reading is unnecessary and can cause the writing process to become seriously inefficient. 

<!--Large projects need infrastructure..a segway to solution st 3 pr 2 -->
Massive building projects require large amounts of infrastructure. The same goes for writing projects, and I suspect that this is even more the case with academic writing. Here is my advice for students writing their dissertations. It's what worked for me. Hopefully, it works for you too!

## A Solution <!--section: Solution st 3 pr 1 -->
<!-- Introduction to the notion of comment strings for those not familiar. st 3 pr 1 -->
My infrastructure solution relies on *comment strings*. Now if you've only written using WYSIWYG (What You See Is What You Get) document editors such as Word then this will be unfamiliar to you. In other document editing frameworks such as LaTeX and Markdown the document which you edit (essentially a text file) gets post-processed into a different format (usually PDF or HTML) which you would show to readers. In this kind of framework, a line or section of text can be marked so that it does not appear in the final, processed version.
For example, in the LaTeX framework, you would use prefix a line with %, e.g.  <br> 
\# This is a comment in LaTeX,<br> 
and in Markdown you would surround the text with angular brackets, e.g. <br> 
\<\!-- This is a comment in Markdown\--> <br> 
These comments will live in the text document forever but never show up in the processed PDF versions.

I'll talk more about writing software later!

<!-- Shorthand pr 1 st 3-->
Above every section, every subsection, and every paragraph, I have a comment string. The first and most important part of the comment consists of a shorthand description of the associated text for the writer's eyes only. For example, above this paragraph, I have the single word 'shorthand'. Upon reading this one word, I know what this paragraph is about - explaining shorthand. I do not expect anyone else besides me to be able to understand these small phrases. Another example is the previous paragraph which was prefixed by the shorthand 'Introduction to the notion of comment strings for those not familiar'. This is slightly longer but it's still a lot easier to read than the entire paragraph. This has a dual function of providing a skeleton layout of your document and radically reducing read time. 

<!-- Completion Status pr 1 st 3-->
In order to know how complete the text associated with the comment is, I include a number taking values 1-3, where (1 is least complete and 3 is totally complete). I call this the *Completion Status* (st in my shorthand) so at the end of the shorthand phrase indicating what the text does there is an 'st x'. This means that I do not have to re-read anything to check if it is complete. Once it's at 3, I do not have to read it again until the final edits and proofreading. 

<!-- Priority Status pr 1 st 3-->
Sometimes, I find that obsessively editing a fluffy paragraph in my introduction is cognitively easier than facing the strain of writing down my core argument. In order to know what I should work on next, I use the completion status along with another number taking values 1-3, which I call the *Priority Status* (pr in my shorthand). The priority status indicates the centrality of the associated text with respect to the core argument and my convention is that 1 is most important and 3 is least important. So in order to know what to work on next, I go through the document and check which is the most important, least complete points and I focus on those first. The aim is that only after finishing the highest priority points till full completion (i.e. writing down the core argument) do I move on to priority 2 and then priority 1.

<!--  Status Hierarchy pr 1 st 3-->
Higher level of structure, e.g. sections and chapters, will also have their own comment strings with statuses. Usually, I will assign the priority status of a section/chapter as the highest priority and least complete component within them.

<!-- Folding pr 1 st 3-->
I usually find looking at a full wall of text intimidating. Should I starting read it all? There is a lot of information seeking to inundate a limited attention span. To orientate myself, I like to use text folding. This means that with a click next to a comment string, all the associated text will disappear. Another click expands it out again. If I am feeling overwhelmed looking at a document, I fold everything up so that I can only see the section titles and comment strings, then I can look at the status and see which is the most pressing section. I repeat this process until I am at the paragraph level. This provides a neat ability to zoom in and out of your document. Note that being able to fold your paragraphs is not a pre-requiste for using the rest of the strategy - it's more of an add-on.


<!--Platforms pr 2 st 3 -->
There are many different platforms which can facilitate such a structure. I wrote my thesis with [TexStudio](https://www.texstudio.org) which uses LaTeX. I loved it because it had great text-folding support. Funnily enough, I am actually writing this post as a Markdown document in [VSCode](https://code.visualstudio.com) which is a great code editor so naturally, it has great folding support. 

The online LaTeX platform [Overleaf](https://www.overleaf.com) has collapsible subsections, and you can also separate your thesis based off chapters.


One should probably be able to implement a hacky version of comments in a Word. If anyone manages to do this, let me know and I'll add it to this post. As a starter, my brother tells me that Microsoft word has collapsible headings.

 
## Integration with other strategies <!--section: Notes st 3 pr 2 -->

Sometimes I like to approach writing through multiple strategies. I try one, if it doesn't work, I try another that gets me bit further, and so on. For instance, if I haven't looked at the content in a while and I am staring down a blank page, I may try free-writing first to prime myself on the content. By free-writing, I mean, writing without editing, proper punctuation or grammar, and with as little internal critique as I can manage - essentially aiming to maximise the quantity of raw content. After free-writing, then I might start sketching out some structure. Other strategies I use include reading similar works, thinking while on a walk or hashing out the logic on a whiteboard. So take this as one strategy of several that you have in your writing toolbox.

 If anyone experiments with this, please let me know, - and good luck with your writing!