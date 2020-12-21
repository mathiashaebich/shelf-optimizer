# shelf-optimizer

Idea for a software that uses AI methods to optimize the order of books in a bookshelf.

## Summary

This software will optimize the order of books in a bookshelf, taking into account the size and various other attributes of the books, and the configurability and constraints of the shelf itself.

## Background

A book is characterized by several attributes that might determine its ideal place in a bookshelf: its author, title, and section, but also its physical dimensions, since space in a bookshelf is scarce. The bookshelf itself is typically configurable in that some or all of its planks can be moved vertically in discrete steps, accomodating higher or shorter books.

An ideal bookshelf would contain all its books, sorted into its respective sections, ordered by its author. However, this could mean that few large books that are widely distributed would take up and actually waste a lot of space, since they would require a large distance of the individual planks in many places. One could choose to group all or some of those large books together, thus only requiring such a large plank distance only in a few placing. But that would disturb the order ... Or one could choose to discard some few books, but for which ones will this actually help getting all books in place?

That's where the shelf-optimizer comes in. It will search the space of all possible arrangements of books for an “optimal” solution, where optimality is defined by penalizing any deviance from the ideal state described above.

... TODO: Describe all possible deviations
TODO: Describe valuation problem

## How is it used?

## Data sources and AI methods

## Challenges

## What next?

## Acknowledgments

# notes to be included
## Eingabe
Liste der Bücher mit Höhe, Dicke, Kategorie, Sortierschlüssel 1 (z.B. Autor), Sortierschlüssel 2 (z.B. Titel), „Wichtigkeit“
Konfiguration des Bücherregals: Spaltenbreiten, Spaltenhöhen, Brettdicken, Konfigurierbarkeit
## Ausgabe
Optimale Konfiguration des Bücherregals und Sortierung der Bücher
## Methodik
Simulated Annealing, evolutionäre Algorithmen?
## Herausforderungen
Die Daten müssen händisch erfasst werden
Das Datenmodell ist relativ komplex
Die Bewertungsparameter müssen richtig gewählt werden
## Possible Extensions
Use AI to find the best valuation parameters for this method
