# shelf-optimizer

Idea for a software that uses AI methods to optimize the order of books in a bookshelf.

## Summary

This software will optimize the order of books in a bookshelf, taking into account the size and various other attributes of the books, and the configurability and constraints of the shelf itself.

## Background

### General Description

A book is characterized by several attributes that might determine its ideal place in a bookshelf: its author, title, and section, but also its physical dimensions, since space in a bookshelf is scarce. The bookshelf itself is typically configurable in that some or all of its planks can be moved vertically in discrete steps, accomodating higher or shorter books.

An ideal bookshelf would contain all its books, sorted into its respective sections, ordered by its author. However, this could mean that few large books that are widely distributed would take up and actually waste a lot of space, since they would require a large distance of the individual planks in many places. One could choose to group all or some of those large books together, thus only requiring such a large plank distance only in a few placing. But that would disturb the order ... Or one could choose to discard some few books, but for which ones will this actually help getting all books in place?

That's where the shelf-optimizer comes in. It will search the space of all possible arrangements of books for an “optimal” solution, where optimality is defined by penalizing any deviance from the ideal state described above.

### Possible Deviations

The algorithm may choose to deviate from the ideal order in the following ways:

* Sorting a book according to its title instead of its author
* Putting a book in a different spot altogether. The penalty will increase with the distance to the proper spot
* Lying a book on its side (and possibly stacking other books on it). The penalty will be per stack instead of per book.
* Defining subcategories and sorting the books inside these subcategories. Without further information about the books, these subcategories can only be according to the dimensions of the books.
* Discarding a book entirely.

Penalties will also apply for very densely packed shelves and for shelves that have large holes in the midst of a section.

This list might be extended in further development.

### Possible shelf configurations

The algorithm may also, without penalties, arrange the planks of the shelf according to given constraints (which model the holes for the movable planks and the presence of fixed planks).

This list might also be extended in further development.

### The Valuation Problem

It is of course unclear how the penalties should be balanced. In fact, choosing the penalties actually appears to be the harder problem compared to the sorting problem (with given penalties). Therefore, we imagine a two-layer architecture:

* The Sorting Layer expects as input all the data described above (including the penalties) and outputs an ordering of the books and configuration of the shelf it deems optimal.
* The Valuation Layer will expects as input the data described above, but _without_ the penalties, and will try to guess good values for the penalties by choosing them according to some algorithm and presenting the corresponding optimal sorting (done by the Sorting Layer) to the user, who can give their feedback. The user can thus train the algorithm to guess penalties that match the user's preferences.

## How is it used?

First, the user has to input all the data about the books and the shelf. Then they will have to rate different sortings done by the Sorting Layer with penalties determined by the Valuation Layer, until they find a sorting they like.

The penalties used for this sorting should be stored and used as a starting point for later arrangements.

## Data sources and AI methods

This algorithm does not use a “big data” approach, so all data are specific to the instance of the problem at hand. In particular, these are:
* a list of all books with the following data: author, title, section, physical dimensions
* the dimensions of the bookshelf, including fixed walls and planks, the thickness of each plank, and the distance between the holes for the movable planks

The AI methods suitable for this project are probably simulated annealing, genetic algorithms, and similar methods.

## Challenges

### Challenges in Implementation

The data model for the shelf might be challenging to implement in a way that allows for efficient optimization.

### Challenges in Using shelf-optimizer

The biggest challenge is that it is extremely cumbersome for the user to enter all the relevant data of all the books and also the shelf. Many book owners might rather choose to just give it a try on their own.

### Putting the “I” back in “AI”

The model for sorting the books described above is actually quite restrictive. A human book owner might come up with very creative ideas how to manage their bookshelf that are not accounted for by our model.

It would be a great improvement to make the model flexible enough to come up with solutions that are not necessarily foreseen by the developer, e.g. using a physics engine and treating the books and the shelf as actual physical entities.

## What next?

These are the next steps:
1. Describe the data model in more detail.
2. Create some date for testing.
3. Develop a prototype.

## Acknowledgments

Thanks to the “[Building AI](https://buildingai.elementsofai.com/)” course which forced me to come up with this idea.


