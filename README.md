# RDF/Turtle Formatting Style Ontology

This OWL ontology defines a vocabulary for the description of settings for pretty-printing a
RDF/Turtle document.

- The ontology is defined in [turtle-formatting.ttl](turtle-formatting.ttl)
- An example for using the vocabulary to define a RDF/Turtle formatting style is given in
  [style1.ttl](style1.ttl)
- [SHACL](https://www.w3.org/TR/shacl/) shapes for validating a style are defined in
  [turtle-formatting-shapes.ttl](turtle-formatting-shapes.ttl)

# Validating a Formatting Style manually

You can easily create your own style by copying and modifying the example file
`style1.ttl`. The following ways can be used to validate a style, shown here by
validating `style1.ttl` as an example:

* Download [Apache Jena](https://jena.apache.org/), and have its `bin` directory in your `PATH`.
  Jena comes with a script called `shacl`, that can be used as follows:
  ```bash
  shacl v --shapes turtle-formatting-shapes.ttl --data turtle-formatting.ttl --data style1.ttl
  ```
  Note that both your style file and the formatting ontology need to be given as data files.

  **Attention:** As of now, Apache Jena's SHACL engine does not validate SPARQL Constraints. This
  means that rules regarding indent sizes in the formatting shapes will not be evaluated.

* Download [Topbraid's SHACL engine](https://github.com/TopQuadrant/shacl) and
  have its `bin` directory in your `PATH`, as described on that page. Download
  [Apache Jena](https://jena.apache.org/), and have its `bin` directory in your
  `PATH`, because we require the `riot` tool that comes with Jena. Then call the
  validation as follows:
  ```bash
  shaclvalidate.sh -shapesfile turtle-formatting-shapes.ttl -datafile <(riot --out=ttl turtle-formatting.ttl style1.ttl)
  ```

# Formatting an arbitrary RDF/Turtle using a Formatting Style

TBD :)

# License

Apache 2.0

# Author

Andreas Textor <[mail@atextor.de](mailto:mail@atextor.de)>
