# DataCamp template course
**You can reach the course on *DataCamp* [here](https://www.datacamp.com/teach/repositories/51113129/go).**

This an automatically generated template course on [DataCamp](https://www.datacamp.com). You can use this as a reference on how to generate your own courses and host them on DataCamp.

If you edit files in this *GitHub* repository, changes will automatically be pushed to *DataCamp*. The changes will trigger a build attempt. After a succesful build, the changes will be visible on your course on *DataCamp*. You can check the build info at [DataCamp Teach](https://www.datacamp.com/teach). You have to be logged in with an account that is linked to this *GitHub* account.

The sections below will give you a clear idea on how to edit the course and which files are important. There will be references to additinal documentation as well.

## Git integration
The strenght of this system is the fact that it will automatically update your [course on DataCamp](https://www.datacamp.com/teach/repositories/51113129/go) each time you push changes to *GitHub*. This means you can enjoy all the advantages of working in a [git](https://git-scm.com/) repository while building your course.

You can edit these simple, version-controlable markdown files and everything will automatically be uploaded to *DataCamp* for you.

You can check out this blog post about [how to create a course with this system](https://www.datacamp.com/community/blog/create-your-own-r-tutorials-with-github-datacamp) and this one about [interpreting the build attempts](https://www.datacamp.com/community/blog/create-your-own-r-tutorials-with-github-datacamp).

## Course file

The first important file in this directory is `course.yml`. This file contains all information about your course file. In this template, it is filled with some default information.

The course file follows the [YAML](http://docs.ansible.com/ansible/YAMLSyntax.html) syntax. The `course.yml` file contains the following options:

- **title**: the course title
- **author_field**: the author of this course
- **description**: a brief description of the course. You can use *HTML* tags to induce new lines (`<br>`), use hyperlinks (`<a href="...">...</a>`), ...

And can be extended with the following optional options:

- **author_bio**: a short bio of the author of this course. You can use *HTML* tags here, like with the **description** option.
- **university**: the university or company this course is made for.
- **difficulty_level**: a number representing the difficulty of the course. This can be **1** (*Beginner*), **2** (*Intermediate*) or **3** (*Advanced*).
- **time_needed**: the expected time needed to finish this course. This option can contain something like: **3 hours**

You can always check the [Teach Documentation on the course file](http://docs.datacamp.com/teach/course-creation.html#the-course-file) to see whether new possible options were added.

In this template course you will see some basic information filled in for these options in the `course.yml` file. You can use this as a guideline.

## Chapter files

Other than the course file, your course repository contains chapter files, named `chapter#.md` or `chapter#.Rmd`, with `#` as the number of the chapter. The chapter files in your repository can not skip a chapter. For example having `chapter1.md` and `chapter3.md`, but not `chapter2.md`, will lead to a failed build on *DataCamp*.

The template course in this repository contains one chapter file: `chapter1.md`. This basic chapter file will help you understand the basics of the *markdown* format used by *DataCamp*.

### Chapter header
The top of the chapter file contains another section which follows a *YAML* syntax. This is similar to what was in the `course.yml` file, but this time the *YAML* header is part the chapter markdown file.

The *YAML* header of the chapter files can contain the following options:

- **title**: the title of the chapter
- **description**: a brief description of the chapter. You can use *HTML* tags here as well.
- **attachments**:
 + **slides_link**: a link to the slides of this chapter

If you make errors against the YAML syntax, your course build may fail. So watch out!

For more information about the chapter file header you can use the [Teach Documentation on chapter files](http://docs.datacamp.com/teach/course-creation.html#the-chapter-files)

### Chapter exercises
Each chapter file contains tags to divide it into exercises. For a detailed documentation on the structure used in these files, you can use the [Teach Documentation on exercises](http://docs.datacamp.com/teach/code-datacamp-exercises.html).

## Grading exercises
### R
An important part of a *DataCamp* course is grading the interactive exercises. This happens with the so-called Submission Correctness Tests, or SCTs. For *R*, they are written using [`testwhat`](https://github.com/datacamp/testwhat), a package specifically designed to correct *DataCamp* exercises.

Basically, this system will compare parts of the code that the student submitted with the solution code.

Two extremely powerful functions in the `testwhat` package are `test_object()` and `test_function()`. `test_object()` compares the value of a variable in the student's environment after the execution of the code with the value of that same variable in the solution environment. `test_function()` allows us to check whether a function is used correctly.

An example of an SCT can be found in the default `chapter1.md` file of this course template.

To learn how to write SCT's yourself, check out the [Teach Documentation on SCT design for R](http://docs.datacamp.com/teach/sct-design-r.html).

### Python (in progress)
For *Python*, the SCT writing works similar to that of *R*. The package that checks for the correctness of *Python* code is called `pythonwhat`.

Like with `testwhat`, `pythonwhat` contains the functions `test_object()` and `test_function()` and they have a similar effect.

To learn how to write SCT's yourself, check out the [Teach Documentation on SCT design for Python](http://docs.datacamp.com/teach/sct-design-python.html).

*Have fun teaching!*