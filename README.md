# NOMEN

NOMEN is a nomenclatural ontology for biological names (not concepts).  

## Overview
The governed rules of biological nomenclature are complex and varied.  NOMEN seeks to provide a stable, logically defined basis for applying these rules to names (strings of text). NOMEN _says nothing about taxa_ (biological entities). Using it will not help you determine, for example, which taxa (biological entities) are real, accepted, well defined, or extinct. The rules encoded in NOMEN are strictly tied to corresponding rules of nomenclature, at present the [ICZN][1], [ICN][2], [ICTV][6], and [ICNP][7].  

NOMEN consists of primarily of two types of data.  Classes classify instances of names (things like the string "Apis melifera") and Object Properties define relationships between those instances.


## Is NOMEN ready for use?
Yes. While NOMEN is certainly evolving we are following best practices that deprecate (not delete) aspects that change.  These deprecations will come with information on how to use new "replacement" classes. In this regard it is safe to start using NOMEN by referencing its URIs.

We will tag NOMEN with a 1.0 prior to submitting a paper detailing it.  


## How can I see what NOMEN contains?
NOMEN is an OWL ontology, it can be read using [Protégé][4]. In a short time we hope to have it picked up by services like ONTOBEE and others, these provide browsing mechanisms.


## How should I use NOMEN?
NOMEN arose in part out of frustration in reconciling bespoke data that included complex tables of nomenclatural statuses.  Theses status were subtly different across applications, and almost never logically exclusive from one another.  Users should think of using NOMEN to annotate their data, these annotations are _assertions_ by an authority (you!).  The foremost role of NOMEN is to help keep those assertions logically consistent.  In brief, any given name is an "instance", and instances can be classified into categories. If you add instance data to NOMEN, and include assertions on those instances, then we can using a reasoning engine to ensure that your assertions are logically consistent with one another.  A trivial example would be to create an instance of a name and assert that it is both valid (`http://purl.obolibrary.org/obo/NOMEN_0000224`) and invalid (`http://purl.obolibrary.org/obo/NOMEN_0000226`). When a reasoner is used on this data it would detect the fallacy, and map how it came about. While we would rarely make this specific mistake (asserting a name is both valid and invalid), there are many other subtleties that have downstream logical consequences that are not so obvious.  NOMEN allows you to classify your data (make assertions), and then be confident that your assertions are consistent with one another.

### Basic application
To start with, think of names as monomials. The name concept in NOMEN is perhaps unique, we think of names as "protonyms", which draw strongly, but perhaps not completely from the idea of basionyms, and from Pyle's concept of usage. Classes are applied to names when you want to assert something about that name in the absence of a reference to another name.  Object properties ("relationships") define a relationship between two names. Therefor all application of NOMEN starts with by answering the question, "Does my assertion reference one or two names?". Representation of the data is straightforward, everything collapses down to a graph, with nodes being names that have attributes (classes from NOMEN) and properties (relationships between names). 

#### Example 1: 'Aus is a name for a genus of animals'
Start by answering the initial question, one, or two names? In this case it's obviously one. Therefor you'll be referencing a class (classifying your name) as opposed to a object property (relationship).  You'll use `http://purl.obolibrary.org/obo/NOMEN_0000307` (ICZN Genus) as the annotation of your name.

#### Example 2: 'Aus bus is a synonym of Bus cus'
Start by answering the initial question, one, or two names? Your assertion is the name 'bus' is a synonym of 'cus'.  Note the assertion is not "Aus bus" is a synonym of "Bus cus".  The relationship between "Aus" and "bus" is itself another assertion. While there are finer levels of granularity using the expression "`bus` `http://purl.obolibrary.org/obo/NOMEN_0000307` (ICZN Synonym) `cus` will work. When making an assertion of "synonymy" (in some general sense) the "incorrect" (for lack of a better cross-nomenclature label) name is on the left (i.e. the subject), and the "correct" name is on the right (i.e. the object). NOMEN includes domain and range assertions in its object properties. In this case the instance in the domain (left side of the expression) is classified as `http://purl.obolibrary.org/obo/NOMEN_0000226` (ICZN Invalid).

#### Example 3: "Aus bus is invalid"
Start by answering the initial question, one, or two names? In this case the assertion is simply "bus" is invalid. Why?  We don't know, we don't what name is the valid name for "bus". Since only one name is referenced in your assertion you'll apply a NOMEN class as its status. NOMEN has multiple subclasses that will let you infer the status of the name is invalid, in this case you can keep it simple and use `http://purl.obolibrary.org/obo/NOMEN_0000226` (ICZN Invalid).  Classes inherit from those above them, so asserting a name is `ICZN unavailable` also means it is `ICZN invalid`.  This lets curators make one assertion that can be used to infer many statuses.

This particular assertion may seem to be curious. Why would we assert that the name is invalid, but not reference the valid name (i.e. use an object property). NOMEN lets you assert the whole history of what has been done by piling up your facts.  At some point there may be conflicting opinions, Sue say invalid, Jane says valid.  Rather than choosing one fact we in practice record both, then we can assert, as curators, that we prefer one or the other by using a status like "invalid" on one of the names, or, more commonly the approach is to assert the validity of the "correct" name.  The cumulative set of facts can be tested for consistency, in theory, by inferring over all of them.

## Citing
NOMEN is presently authored by Dmitry Dmitriev and Matt Yoder. Major conceptual contributions came from Rich Pyle. Its development is supported by the Species File Group. A suggested citation is `Dmitriev, D.A. and Yoder, M. NOMEN. <accessed on>. Available at https://github.com/SpeciesFileGroup/nomen.`

## Contributing
NOMEN is intended to be a community resource.  We welcome all aspects of its development, from assiting in its curration to helping to apply it practically.  The most straightforwad mechanism for asking questions, reporting problems, or requesting additions to the ontology is the [issue tracker][3].  Alternately there is a [listserv][5].  

## Funding
This project was funded in part by NSF-ABI-1356381.  Any opinions, findings and conclusions or recommendations expressed in this material are those of the author(s) and do not necessarily reflect the views of the National Science Foundation. 

[1]: http://iczn.org/
[2]: http://www.iapt-taxon.org/nomen/main.php
[3]: https://github.com/SpeciesFileGroup/nomen/issues  
[4]: http://protege.stanford.edu/
[5]: https://groups.google.com/forum/#!forum/nomen-discuss
[6]: https://talk.ictvonline.org/
[7]: http://www.the-icsp.org/

