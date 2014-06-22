Reveal.js-TOC-Progress
======================

LaTeX Beamer-like progress indicator according to table of contents for Reveal.js HTML presentations

#Description

##What is Reveal.js-TOC-Progress?

Reveal.js-TOC-Progress is a plugin for the Reveal.js framework for HTML presentations (https://github.com/hakimel/reveal.js).

##What does Reveal.js-TOC-Progress do?

Reveal.js-TOC-Progress includes a footer in all the slides of a Reveal.js presentation (with optional exclusion of some slides) that will show the progress in relation to the table of contents, in a similar way as in a LaTeX-Beamer presentation.

##Behaviour

The footer has two columns. The left column shows a list of the main sections (except those we explicitly tell to ignore), highlighting the section we are now in. The right column shows the subsections of the main section we are now in (again with the option of ignoring those we do not want to show), highlighting the subsection we are currently at.

##Configurable options

The behaviour for too long section or subsection lists is configurable. The font of the text can be reduced to make the list fit in the footer, or the list will scroll when necessary.

The background color of the footer is also configurable.

#Installation

##Necessary files

The ```toc-progress``` folder of the ```plugin``` folder has to be copied to the ```plugin``` folder of the Reveal.js presentation.

##CSS

The CSS of the Reveal.js-TOC-Progress plugin is included dynamically when it is initialized. However, if we configure the presentation not to include the Reveal.js-TOC-Progress footer in the first page, this will be shown until the CSS is loaded dynamically, causing an ugly effect. To avoid it, include the CSS in the header of the Reveal.js presentation, with this line:

```<link rel="stylesheet" href="plugin/toc-progress/toc-progress.css">```

##Plugin initialization

Include Reveal.js-TOC-Progress among the Reveal.js plugin initializations, like this:

```javascript
Reveal.initialize
(
	{
		...
		dependencies:
		[
			...
			{ src: 'plugin/toc-progress/toc-progress.js', async: true, callback: function() { toc_progress.initialize(); toc_progress.create(); } }
		]
	}
);
```

##Customization

The ```toc_progress.initialize``` function can take two parameters:

- ```reducescroll```: if ```'reduce'```, the font of the text of too long section or subsection lists is reduced to make the list fit in the footer; if ```'scroll'``` (default), the list will scroll when necessary.
- ```background```: a string of the form ```'rgba(0,255,0,0.1)'```, for the background colour of the footer.

Including the ```toc_progress.create``` function in the Reveal.js initialization is not compulsory. If it is not included, the key ```q``` has to be pressed to create the footer.

For further customization (like making the footer a header, for example), arrange the ```plugin/toc-progress/toc-progress.css``` file accordingly.

#Use

##Titles

The Reveal.js-TOC-Progress plugin works in the same manner as the Presentable plugin (http://fcfeibel.com/presentable). It takes the first ```h1```, ```h2``` or ```h3``` tag from the slides as the titles for the table of contents. Main sections will be the titles of the first slide in each vertical section and secondary sections will be the rest of the titles.

##Title exclusion

A title will be excluded from the table of contents if we put it a ```class``` attribute with a value of ```no-toc-progress```.

##Exclusion from slides

Likewise, the Reveal.js-TOC-Progress footer will not be shown in a slide if the corresponding section has a ```data-state``` attribute with a value of ```no-toc-progress```.

##Optional deletion and recreation at any time

Pressing the ```q``` key causes the Reveal.js-TOC-Progress footer to disappear. Pressing the ```q``` key again creates it again.

#Links

- Source code on GitHub: https://github.com/e-gor/Reveal.js-TOC-Progress
- Demo presentation with Reveal.js-TOC-Progress: http://e-gor.github.io/Reveal.js-TOC-Progress/demo

#License

GPL v3 (http://www.gnu.org/copyleft/gpl.html).
