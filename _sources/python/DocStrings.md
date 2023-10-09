(Chap_DocStrings)=
# Docstrings and Documentation

```{prf:observation} Eagleson's Law of Programming
:label: ObsDocStrings_Eagleson
> "Any code of your own that you haven't looked at for six or more months might as well have been written by someone else."[^EaglesonsLaw]
```

```{prf:observation} Guido van Rossum on clear code
:label: ObsDocStrings_Guido
> "Code is more often read than written."[^Guido]
```

Good documentation is critical to the ability of yourself and others to understand and disseminate your work and to allow others to reproduce it. As Eagleson's Law of Programming implies in {prf:ref}`ObsDocStrings_Eagleson` above, one of the biggest benefits of good documentation might be to the core maintainers and original code writers of a project. Despite the aspiration that the Python programming language be easy and intuitive enough to be its own documentation, we have often found than any not-well-documented code written by ourselves that is only a few months old is more likely to require a full rewrite rather than incremental additions and improvements.

Python scripts allow for two types of comments: inline comments (which are usually a line or two at a time) and docstrings, which are longer blocks set aside to document the source code. We further explore other more extensive types of documentation inclding README files, Jupyter notebooks, cloud notebooks, Jupyter Books, and published documentation forms.

A good resource is the RealPython tutorial entitled, "[Documenting Python Code: A Complete Guide](https://realpython.com/documenting-python-code/)" {cite}`Mertz:2023`.


(SecDoc_comments)=
## Inline comments

Put inline comments here. "[PEP 257--Docstring Conventions](https://peps.python.org/pep-0257/)" differentiates between inline comments, which use the `#` symbol, and one-line docstrings, which use the `"""..."""` format {cite}`GoodgerVanRossum:2001`.


(SecDoc_docstrings)=
## Docstrings

"[PEP 257--Docstring Conventions](https://peps.python.org/pep-0257/)" give suggested format and usage for docstrings in Python {cite}`GoodgerVanRossum:2001`. Docstrings also have the power to help with automatric documentation of your codes API. Talk about sphinx and docstring styles (e.g., google and Numpy)...

Put something here about the LaTeX equations in the docstrings that get automatically compiled into the API section of `OG-Core`.



(SecDoc_README)=
## README file

Put usage of `README` file as documentation here.


(SecDoc_JupNote)=
## Jupyter notebooks

Put discusion of Jupyter notebooks here.


(SecDoc_CloudNote)=
## Cloud notebooks

Put discusion of Google Colab and other types of cloud notebook platforms here.


(SecDoc_JupBook)=
## Jupyter Book documentation

Put discusion of Jupyter Book documentation here.


(SecDoc_Other)=
## Other published documentaiton

Put discusion of other forms of published documentation here such as white papers, peer-reviewed articles, websites (readthedocs by Sphinx).


(SecDocstringExercises)=
## Exercises

```{exercise-start}
:label: ExerDoc-inline
```
Inline comment excercise
```{exercise-end}
```

```{exercise-start}
:label: ExerDoc-google
```
Use Google docstring style to format a function that is the FOC_savings function (worked with in SciPy exercises)
```{exercise-end}
```

```{exercise-start}
:label: ExerDoc-sphinx
```
Create auto documentation of (2) with Sphinx?
```{exercise-end}
```

```{exercise-start}
:label: ExerDoc-??
```
Other??
```{exercise-end}
```


(SecDocstringFootnotes)=
## Footnotes

The footnotes from this chapter.

[^EaglesonsLaw]: We could not find a proper citation for the source of this quote "Eagleson's Law of Programming". Some entries on this thread entitled "[Who is Eagleson and where did Eagleson's law originate?](https://ask.metafilter.com/200910/Who-is-Eagleson-and-where-did-Eaglesons-law-originate)" suggest that the quote is at least as old as 1987 and is likely from [Peter S. Eagleson](https://en.wikipedia.org/wiki/Peter_S._Eagleson), a member of the MIT faculty since 1952. However, neither the date, nor the author is confirmed.

[^Guido]: This is a quote from Guido van Rossum, the original creator of the Python programming language, supposedly from an early PyCon conference. This quote is referenced in one of the early Python Enhancement Proposals, "[PEP 8--Style Guide for Python Code](https://peps.python.org/pep-0008/)" {cite}`VanRossumEtAl:2001`.
