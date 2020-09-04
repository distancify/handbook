[Handbook](../../README.md) / Standard Operating Proceedures / Implementer

# Create Development Branch

Before the work of implementing a feature can begin, you must create a source branch where that work can be written in isolation.

Branches and the way we organize them is the back bone of the quality control and how software is shipped. Therefor it's **very** important to pay close attention to where, when and how you name a branch for that control not to be lost.

## Different types of software

The way we ship or deploy software differs somewhat between whay type of project you're working in. We make the main distinction between *SaaS* and *Shipped software*.

### SaaS

**SaaS** projects are services that usually runs on hardware controlled and maintained by us. There's only a single "instance" of a SaaS service, even if they all have various test environments. The most common SaaS project you will encounter at Distancify is a customer e-commerce website, but there are others as well.

A **SaaS** service generally only have a single version in production at any given time.

![SaaS Branching](https://app.lucidchart.com/publicSegments/view/74994a86-3922-4197-b714-c4a0a8738d0b/image.png)

### Shipped Software

**Shipped Software** is software that is shipped as a package to be used in other projects. Libraries fall within this category, but also applications that runs on the user's machine fall into this category.

A **Shipped Software** has multiple versions that must be maintained in parallell, as different consumers might be updating to newer versions in a non coherent fashion.

![Shipped Software Branching](https://app.lucidchart.com/publicSegments/view/d99bf5d7-bc4a-45c2-8566-ff2cfe02b251/image.png)