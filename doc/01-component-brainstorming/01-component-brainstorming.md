# Portfolio Part 1: Component Brainstorming

- **Name**: Miles Conner
- **Dot Number**: Conner.232
- **Due Date**: 9/16 @ 3:00 PM EST

## Assignment Overview

The overall goal of the portfolio project is to have you design and implement
your own OSU component. There are no limits to what you choose to design and
implement, but your component must fit within the constraints of our software
sequence discipline. In other words, the component must extend from Standard and
must include both a kernel and a secondary interface.

Because this is a daunting project, we will be providing you with a series of
activities to aid in your design decisions. For example, the point of this
assignment is to help you brainstorm a few possible components and get some
feedback. For each of these components, you will need to specify the high-level
design in terms of the software sequence discipline. In other words, you will
describe a component, select a few kernel methods for your component, and select
a few secondary methods to layer on top of your kernel methods.

You are not required to specify contracts at this time. However, you are welcome
to be as detailed as you'd like. More detail means you will be able to get more
detailed feedback, which may help you decide which component to ultimately
implement.

## Assignment Checklist

To be sure you have completed everything on this assignment, we have littered
this document with TODO comments. You can browse all of them in VSCode by
opening the TODOs window from the sidebar. The icon looks like a tree and will
likely have a large number next to it indicating the number of TODOS. You'll
chip away at that number over the course of the semester. However, if you'd
like to remove this number, you can disable it by removing the following
line from the `settings.json` file:

```json
"todo-tree.general.showActivityBarBadge": true,
```

Which is not to be confused with the following setting that adds the counts
to the tree diagram (you may remove this one as well):

```json
"todo-tree.tree.showCountsInTree": true,
```

## Assignment Learning Objectives

Without learning objectives, there really is no clear reason why a particular
assessment or activity exists. Therefore, to be completely transparent, here is
what we're hoping you will learn through this particular aspect of the portfolio
project. Specifically, students should be able to:

1. Integrate their areas of interest in their personal lives and/or careers with
   their knowledge of software design
2. Determine the achievablility of a software design given time constraints
3. Design high-level software components following the software sequence
   discipline

## Assignment Rubric: 10 Points

Again, to be completely transparent, most of the portfolio project, except the
final submission, is designed as a formative assessment. Formative assessments
are meant to provide ongoing feedback in the learning process. Therefore,
the rubric is designed to assess the learning objectives *directly* in a way
that is low stakes—meaning you shouldn't have to worry about the grade. Just
do good work.

1. (3 points) Each design must align with your personal values and long-term
   goals. Because the goal of this project is to help your build out a
   portfolio, you really ought to care about what you're designing. We'll give
   you a chance to share your personal values, interests, and long-term goals
   below.
2. (3 points) Each design must be achievable over the course of a single
   semester. Don't be afraid to design something very small. There is no shame
   in keeping it simple.
3. (4 points) Each design must fit within the software sequence discipline. In
   other words, your design should expect to inherit from Standard, and it
   should contain both kernel and secondary methods. Also, null and aliasing
   must be avoided, when possible. The methods themselves must also be in
   justifiable locations, such as kernel or secondary.

## Pre-Assignment

> Before you jump in, we want you to take a moment to share your interests
> below. Use this space to talk about your career goals as well as your personal
> hobbies. These will help you clarify your values before you start
> brainstorming. Plus it helps us get to know you better! Feel free to share
> images in this section.

My career goals are to design computer hardware or work on low level software (BIOS software, driver software, operating systems, etc). I started out at OSU with ambitions of getting a CS degree to become a game programmer. I spent my free time messing around with game programming and many small, half finished, single level platformers later I found that I was actually more interested in the technology that games run on than the games themselves. I spent lots of time trying to build openGL renderers from scratch and this eventaully led me to a greater interest in computer hardware. Basically annoying internet forms telling me I had to write custom memory allocators and worry about CPU cache misses or I wasn't doing game engine dev right turned me onto the world of computer hardware, a world I enjoy even more than the world of game engines. So I switched my degree to electrical, and some day hope to work for AMD or Intel, designing CPUs. As far as my hobbies are concerned, I'm just a nerd whose life consists entirely of playing video games and doing homework.

My component ideas are inspired by a game of life program that I worked on in high school, a matrix component that's inspired by the matrices I implemented in my computer graphics projects, and a complex number component that I like because it seems to fit the software discipline well and my life has become nothing but complex numbers since I became an ECE student.

## Assignment

As previously stated, you are tasked with brainstorming 3 possible components.
To aid you in this process, we have provided [some example components][example-components]
that may help you in your brainstorming. All of these components were made at
some point by one of your peers, so you should feel confident that you can
accomplish any of them.

There is no requirement that you use any of the components listed above.
If you want to model something else, go for it! Very common early object
projects usually attempt to model real-world systems like banks, cars,
etc. Make of this whatever seems interesting to you, and keep in mind that
you're just brainstorming right now. You do not have to commit to anything.

### Example Component

To help you brainstorm a few components, we've provided an example below of a
component you already know well: NaturalNumber. We highly recommend that you
mirror the formatting as close as possible in your designs. By following this
format, we can be more confident that your designs will be possible.

- Example Component: `NaturalNumber`
  - **Description**:
    - The purpose of this component is to model a non-negative
      integer. Our intent with this design was to keep a simple kernel that
      provides the minimum functionality needed to represent a natural number.
      Then, we provide more complex mathematical operations in the secondary
      interface.
  - **Kernel Methods**:
    - `void multiplyBy10(int k)`: multiplies `this` by 10 and adds `k`
    - `int divideBy10()`: divides `this` by 10 and reports the remainder
    - `boolean isZero()`: reports whether `this` is zero
  - **Secondary Methods**:
    - `void add(NaturalNumber n)`: adds `n` to `this`
    - `void subtract(NaturalNumber n)`: subtracts `n` from `this`
    - `void multiply(NaturalNumber n)`: multiplies `this` by `n`
    - `NaturalNumber divide(NaturalNumber n)`: divides `this` by `n`, returning
      the remainder
    - ...
  - **Additional Considerations** (*note*: "I don't know" is an acceptable
    answer for each of the following questions):
    - Would this component be mutable? Answer and explain:
      - Yes, basically all OSU components have to be mutable as long as they
        inherit from Standard. `clear`, `newInstance`, and `transferFrom` all
        mutate `this`.
    - Would this component rely on any internal classes (e.g., `Map.Pair`)?
      Answer and explain:
        - No. All methods work with integers or other NaturalNumbers.
    - Would this component need any enums or constants (e.g.,
      `Program.Instruction`)? Answer and explain:
        - Yes. NaturalNumber is base 10, and we track that in a constant called
          `RADIX`.
    - Can you implement your secondary methods using your kernel methods?
      Answer, explain, and give at least one example:
      - Yes. The kernel methods `multiplyBy10` and `divideBy10` can be used to
        manipulate our natural number as needed. For example, to implement
        `increment`, we can trim the last digit off with `divideBy10`, add 1 to
        it, verify that the digit hasn't overflown, and multiply the digit back.
        If the digit overflows, we reset it to zero and recursively call
        `increment`.

Keep in mind that the general idea when putting together these layered designs
is to put the minimal implementation in the kernel. In this case, the kernel is
only responsible for manipulating a digit at a time in the number. The secondary
methods use these manipulations to perform more complex operations like
adding two numbers together.

Also, keep in mind that we don't know the underlying implementation. It would be
completely reasonable to create a `NaturalNumber1L` class which layers the
kernel on top of the existing `BigInteger` class in Java. It would also be
reasonable to implement `NaturalNumber2` on top of `String` as seen in
Project 2. Do not worry about your implementations at this time.

On top of everything above, there is no expectation that you have a perfect
design. Part of the goal of this project is to have you actually use your
component once it's implemented to do something interesting. At which point, you
will likely refine your design to make your implementation easier to use.

### Component Designs

> Please use this section to share your designs.

- Component Design #1: `Matrix`
  - **Description**:
    - A component to model a matrix of arbitrary dimensionality (n by m). Methods that return the value of entries in the matrix and mutate the entries would be in the kernel and all of the typical math stuff you can do with matrices would be in the secondary interface (transpose, inverse, etc). If this is too ambitious I could model a matrix of a fixed size (like 3x3), or I could do a vector instead, and have the secondary methods compute dot products, magnitudes, etc. Alternatively, if I wanted to be more ambitious I could layer a matrix component on top of vector components.
  - **Kernel Methods**:
    - `int lengthRows()`: returns number of rows in `this`
    - `int lengthColumns()`: returns number of columns in `this`
    - `double value(int row, int col)`: returns the entry at `(row, col)` in `this`
    - `void setValue(int row, int col, double value)`: sets the entry at `(row, col)` in `this` to `value`
    - `double determinant()`: returns the determinant of `this`
    - `boolean isInvertible()`: returns whether or not `this` is invertible
    - `boolean canBeAdded(Matrix m)`: returns whether or not `m` can be added to `this`
    - `boolean canBeMultiplied(Matrix m)`: returns whether or not `this` can be multiplied by `m`
  - **Secondary Methods**:
    - `void transpose()`: transposes `this`
    - `void invert()`: inverts `this`
    - `void scale(double n)`: multiplies every entry in `this` by `n`
    - `void add(Matrix m)`: adds `m` to `this`
    - `void subtract(Matrix m)`: subtracts `m` from this
    - `void multiply(Matrix m)`: multiplies `this` by `m`
    - `void divide(Matrix m)`: multiplies `this` by `1/m`
  - **Additional Considerations** (*note*: "I don't know" is an acceptable
    answer for each of the following questions):
    - Would this component be mutable? Answer and explain:
      - Yes, `setValue()` in the kernal would mutate it, and every secondary method would mutate it.
    - Would this component rely on any internal classes (e.g., `Map.Pair`)?
      Answer and explain:
      - It would just rely on Java primitives (I'm thinking the entries would probably be doubles) and Java arrays.
    - Would this component need any enums or constants (e.g.,
      `Program.Instruction`)? Answer and explain:
      - No, I don't think it would.
    - Can you implement your secondary methods using your kernel methods?
      Answer, explain, and give at least one example:
      - Yes. Many of the secondary methods would only be defined for certain matrices so my method contracts could be complicated but this is why I included `isInvertible()`, `canBeAdded()`, and `canBeMultiplied()` in the kernel, which themselves would rely on `lengthRows()`, `lengthColumns()`, and `determinant()` because I think that's all you need to check if addition, multiplication, and inversion is defined.


- Component Design #2: `ComplexNumber`
  - **Description**:
    - A component to model a complex number that would accept arguments in polar or rectangular form. The secondary methods would do complex math and report the result in either polar or rectangular form. Quaternions are also an option.
  - **Kernel Methods**:
    - `double real()`: returns the real component of `this`
    - `double imaginary()`: returns the imaginary component of `this`
    - `double magnitude()`: returns the magnitude of `this` in polar form
    - `double angle()`: returns the angle of `this` in polar form
    - `void setValueRectangular(double real, double imaginary)`: sets `this` to (`real` + `imaginary` * i)
    - `void setValuePolar(double magnitude, double angle)`: sets `this` to  (`magnitude` < `angle`)
    - `int quadrant()`: returns the quadrant `this` falls in when `this` is in polar form (1-4)
    - `void toRect()`: updates the rectangular form member variables to be equal to the polar form member variables
    - `void toPolar()`: updates the polar form member variables to be equal to the rectangular form member variables
  - **Secondary Methods**:
    - `void conjugate()`: does complex conjugation to `this`
    - `void add(ComplexNumber z)`: adds `z` to this
    - `void subtract(ComplexNumber z)`: subtracts `z` from `this`
    - `void multiply(ComplexNumber z)`: multplies `this` by `z`
    - `void divide(ComplexNumber z)`: divides `this` by `z`
    - `void scale(double n)`: multiplies `this` by `n`
  - **Additional Considerations** (*note*: "I don't know" is an acceptable
    answer for each of the following questions):
    - Would this component be mutable? Answer and explain:
      - Yes, setting the values from the kernel and all of the secondary methods would mutate it.
    - Would this component rely on any internal classes (e.g., `Map.Pair`)?
      Answer and explain:
      - No, I don't think it would. Just Java doubles.
    - Would this component need any enums or constants (e.g.,
      `Program.Instruction`)? Answer and explain:
      - No, I don't think it would.
    - Can you implement your secondary methods using your kernel methods?
      Answer, explain, and give at least one example:
      - Yes. The secondary methods will use whichever representation (polar or rectangular) is more useful to do the math the method is doing and then call either `toRect()` or `toPolar()` to update the representation that it didn't modify. The `quadrant()` kernel method will be used by `toPolar()` to ensure that tangent gives an angle in the right quadrant.


- Component Design #3: `Cell`
  - **Description**:
    - A component modeling one cell in a cellular automaton, specifically a Conway's game of life cell. It would represent a current state and a next state, with an update method to update the current state to the next state. It would also keep track of its own grid position.
  - **Kernel Methods**:
    - `boolean isAlive()`: returns whether or not `this` is on or off (current state)
    - `void kill()`: sets next state of `this` to off
    - `void giveLife()`: sets next state of `this` to on
    - `void changeState()`: sets current state of `this` to the next state of `this`
    - `int x()`: returns the x position of `this` in the grid
    - `int y()`: returns the y position of `this` in the grid
  - **Secondary Methods**:
    - `int livingNeighbors(Cell[] grid)`: returns how many of the neighboring cells of `this` have a current state of alive
    - `void nextState(int livingNeighbors)`: sets the next state of `this` based on how many living neighbors `this` has
  - **Additional Considerations** (*note*: "I don't know" is an acceptable
    answer for each of the following questions):
    - Would this component be mutable? Answer and explain:
      - Yes, the kernel methods will mutate its state. However, I don't think the grid position would be mutable.
    - Would this component rely on any internal classes (e.g., `Map.Pair`)?
      Answer and explain:
      - Just Java primitives and arrays. The states would be represented with booleans and the grid position with ints. The program using this component would have a big array of cells that it would loop through to update them. A program with a GUI could even display the cell states graphically, although this would require timing if the display was going to update itself over time.
    - Would this component need any enums or constants (e.g.,
      `Program.Instruction`)? Answer and explain:
      - No, the component itself wouldn't. A game of life program using the component might however.
    - Can you implement your secondary methods using your kernel methods?
      Answer, explain, and give at least one example:
      - Yes, the grid positions in conjunction with the current state can be used by `livingNeighbors()` to determine how many living cells neighbor each cell, and `nextState()` can call `changeState()` on each of them to actually make the update happen.

## Post-Assignment

The following sections detail everything that you should do once you've
completed the assignment.

### Changelog

At the end of every assignment, you should update the
[CHANGELOG.md](../../CHANGELOG.md) file found in the root of the project folder.
Since this is likely the first time you've done this, we would recommend
browsing the existing file. It includes all of the changes made to the portfolio
project template. When you're ready, you should delete this file and start your
own. Here's what I would expect to see at the minimum:

```markdown
# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Calendar Versioning](https://calver.org/) of
the following form: YYYY.0M.0D.

## 2024.09.16

### Added

- Designed a `Matrix` component
- Designed a `ComplexNumber` component
- Designed a `Cell` component
```

Here `YYYY.MM.DD` would be the date of your submission, such as 2024.04.21.

You may notice that things are nicely linked in the root CHANGELOG. If you'd
like to accomplish that, you will need to make GitHub releases after each pull
request merge (or at least tag your commits). This is not required.

In the future, the CHANGELOG will be used to document changes in your
designs, so we can gauge your progress. Please keep it updated at each stage
of development.

### Submission

If you have completed the assignment using this template, we recommend that
you convert it to a PDF before submission. If you're not sure how, check out
this [Markdown to PDF guide][markdown-to-pdf-guide]. However, PDFs should be
created for you automatically every time you save, so just double check that
all your work is there before submitting. For future assignments, you will
just be submitting a link to a pull request. This will be the only time
you have to submit any PDFs.

### Peer Review

Following the completion of this assignment, you will be assigned three
students' component brainstorming assignments for review. Your job during the
peer review process is to help your peers flesh out their designs. Specifically,
you should be helping them determine which of their designs would be most
practical to complete this semester. When reviewing your peers' assignments,
please treat them with respect. Note also that we can see your comments, which
could help your case if you're looking to become a grader. Ultimately, we
recommend using the following feedback rubric to ensure that your feedback is
both helpful and respectful (you may want to render the markdown as HTML or a
PDF to read this rubric as a table).

| Criteria of Constructive Feedback | Missing                                                                                                                           | Developing                                                                                                                                                                                                                                | Meeting                                                                                                                                                               |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Specific                          | All feedback is general (not specific)                                                                                            | Some (but not all) feedback is specific and some examples may be provided.                                                                                                                                                                | All feedback is specific, with examples provided where possible                                                                                                       |
| Actionable                        | None of the feedback provides actionable items or suggestions for improvement                                                     | Some feedback provides suggestions for improvement, while some do not                                                                                                                                                                     | All (or nearly all) feedback is actionable; most criticisms are followed by suggestions for improvement                                                               |
| Prioritized                       | Feedback provides only major or minor concerns, but not both. Major and minar concerns are not labeled or feedback is unorganized | Feedback provides both major and minor concerns, but it is not clear which is which and/or the feedback is not as well organized as it could be                                                                                           | Feedback clearly labels major and minor concerns. Feedback is organized in a way that allows the reader to easily understand which points to prioritize in a revision |
| Balanced                          | Feedback describes either strengths or areas of improvement, but not both                                                         | Feedback describes both strengths and areas for improvement, but it is more heavily weighted towards one or the other, and/or descusses both but does not clearly identify which part of the feedback is a strength/area for improvement  | Feedback provides balanced discussion of the document's strengths and areas for improvement. It is clear which piece of feedback is which                             |
| Tactful                           | Overall tone and language are not appropriate (e.g., not considerate, could be interpreted as personal criticism or attack)       | Overall feedback tone and language are general positive, tactul, and non-threatening, but one or more feedback comments could be interpretted as not tactful and/or feedback leans toward personal criticism, not focused on the document | Feedback tone and language are positive, tactful, and non-threatening. Feedback addesses the document, not the writer                                                 |

### Assignment Feedback

If you'd like to give feedback for this assignment (or any assignment, really),
make use of [this survey][survey]. Your feedback helps make assignments
better for future students.

[example-components]: https://therenegadecoder.com/code/the-never-ending-list-of-small-programming-project-ideas/
[markdown-to-pdf-guide]: https://therenegadecoder.com/blog/how-to-convert-markdown-to-a-pdf-3-quick-solutions/
[survey]: https://forms.gle/dumXHo6A4Enucdkq9
