NOMEN
=====

NOMEN is a nomenclatural ontology for biological names (not concepts).  

Overview
--------

The governed rules of biological nomenclature are complex and varied.  NOMEN seeks to provide a stable, logically defined basis for applying these rules to names (strings of text). NOMEN _says nothing about taxa_ (biological entities). Using it will not help you determine, for example, which taxa (biological entities) are real, accepted, well defined, or extinct. The rules encoded in NOMEN are strictly tied to corresponding rules of nomenclature, at present the [ICZN][1] and [ICN][2].  

NOMEN consists of primarily of two types of data.  Classes classify instances of names (things like the string "Apis melifera") and Object Properties define relationships between those instances.


Is NOMEN ready for use?
-----------------------

Yes. While NOMEN is certainly evolving we are following best practices that deprecate (not delete) aspects that change.  These deprecations will come with information on how to use new "replacement" classes. In this regard it is safe to start using NOMEN by referencing its URIs.

We will tag NOMEN with a 1.0 prior to submitting a paper detailing it.  


How can I see what NOMEN contains?
----------------------------------

NOMEN is an OWL ontology, it can be read using [Protégé][4]. In a short time we hope to have it picked up by services like ONTOBEE and others, these provide browsing mechanisms.


How should I use NOMEN?
-----------------------

NOMEN arose in part out of frustration in reconciling bespoke data that included complex tables of nomenclatural statuses.  Theses status were subtly different across applications, and almost never logically exclusive from one another.  Users should think of using NOMEN to annotate their data, these annotations are _assertions_ by an authority (you!).  The foremost role of NOMEN is to help keep those assertions logically consistant.  In brief, any given name is an "instance", and instances can be classified into categories. If you add instance data to NOMEN, and include assertions on those instances, then we can using a reasoning engine to ensure that your assertions are logically consistant with one another.  A trivial example would be to create an instance of a name and assert that it is both valid (`http://purl.obolibrary.org/obo/NOMEN_0000224`)  and invalid (`http://purl.obolibrary.org/obo/NOMEN_0000226`). When a reasoner is used on this data it would detect the fallacy, and map how it came about. While we would rarely make this specific mistake (asserting a name is both valid and invalid), there are many other subtlties that have downstream logical consequences that are not so obvious.  NOMEN allows you to classify your data (make assertions), and then be confident that your assertions are consistant with one another.

Citing
------

NOMEN is presently authored by Dmitry Dmitriev and Matt Yoder. Major conceptual contributions came from Rich Pyle. Its development is supported by the Species File Group. A suggested citation is `Dmitriev, D.A. and Yoder, M. NOMEN. <accessed on>. Available at https://github.com/SpeciesFileGroup/nomen.`


Contributing
------------

NOMEN is intended to be a community resource.  We welcome all aspects of its development, from assiting in its curration to helping to apply it practically.  The most straightforwad mechanism for asking questions, reporting problems, or requesting additions to the ontology is the [issue tracker][3].  Alternately there is a [listserv][5].  


[1]: http://iczn.org/
[2]: http://www.iapt-taxon.org/nomen/main.php
[3]: https://github.com/SpeciesFileGroup/nomen/issues  
[4]: http://protege.stanford.edu/
[5]: https://groups.google.com/forum/#!forum/nomen-discuss

