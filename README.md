# NHS Wales data dictionary

> "Turtles all the way down"
>
> [https://en.wikipedia.org/wiki/Turtles_all_the_way_down](https://en.wikipedia.org/wiki/Turtles_all_the_way_down)

This repository provides machine-readable versions of the NHS Wales data dictionary. It is currently a proof-of-concept.

'Turtles all the way down' refers to the concept of infinite regress, and I'm using it to allude to the fact that, in health and care, it truly is, 'data all the way down'. Structured, meaningful data is the foundation on which we solve problems in health and care. I touched on the fractal, recursive nature of data in ["The Fractal medical record"](https://wardle.org/medical-records/2017/10/08/the-broken-medical-record.html) ; you might also like [this xkcd cartoon](https://xkcd.com/1416/)

## Background

The background to this experiment is outlined in [https://wardle.org/strategy/2020/06/21/more-than-one-side.html](https://wardle.org/strategy/2020/06/21/more-than-one-side.html) and [https://wardle.org/standards/2020/07/09/value-sets.html](https://wardle.org/standards/2020/07/09/value-sets.html).

Value sets are important. In essence, a value set is a set of values that can be used for a data field. 

But unless we can derive meaning from those values in software, value sets can make it difficult to have a shared understanding. 

If we don't address the problem of value sets properly, we might end up with technical interoperability between two different pieces of software code because they can exchange information, but fail to build *semantic interoperability*.

Most value sets don't really have associated semantic information, because they are used as classification systems for central reporting, and don't provide a sound ontological basis with which to work.

Likewise, if we expect clinical systems to use proscribed local proprietary value sets, software developers must bake in those values into their software or build functionality to map to local value sets. Each of these options adds to the cost of integration.

## 'Integration'

How did your web browser integrate with this website? Did they have committee meetings and agree a convergence strategy, or were there a set of standards that both used? In essence, the use of standards permits decoupling of systems so that they can be developed in parallel and independently. That means less coordination and greater pace!

I'd much prefer to see operational systems using meaningful codes derived from an ontology, such as SNOMED CT, because once clinical systems build functionality to use such an ontology, it's very easy to use a subset in a particular context. The advantage is that users can choose terms at the level of specificity they wish, such as pneumonia, or community-acquired pneumonia, or pneumonia due to COVID-19. 

But classification systems are very useful in central reporting and data analysis. They provide a simplified view of granular specific data. 

The logical consequence is that we need systems that can transparently flip between different classification and ontology systems. When we can do that with losing information, it is called ‘round-tripping’, but in many cases it’s not possible to map without losing information because a classification simply doesn’t have the necessary level of granularity. The logical consequence of that is that we should do most of our work in a finely-grained terminology that has an ontological basis and map to less granular, lossy classification schemes for reporting purposes.

Any national data project in health and care needs to give careful consideration to how to process data. In general, real-life health and care data is granular, hierarchical, graph-like and complex, while many central reporting requirements prefer a simpler tabular, categorised view.

As such:

- We need to namespace identifiers used for central reporting to give them meaning
- We need to publish datasets and category definitions in machine-readable formats so that they can be processed
- We need to publish a declarative mapping from one identifier namespace to another if we wish to foster semantic interoperability; an ontology of ontologies.

This repository aims to do that in a computer programming language agnostic manner, by starting with canonical data and providing tools to map those data definitions into different formats, including human-readable formats, automatically.
