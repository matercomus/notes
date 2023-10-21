- Role: provides code for candidate solutions that can be manipulated by variation operators
- Leads to two levels of existence
	- Phenotype: object in original problem context, the outside
	- Genotype: code to denote that object, the inside (chromosome, "digital DNA")
- Implies two mappings:
	- Encoding: phenotype -> genotype (not necessarily one-to-one)
	- Decoding genotype -> phenotype (MUST be one-to-one)
- Chromosomes contain genes, 
	- which are in (usually fixed) **positions** called **loci** (singular: locus) 
	- and have a **value** (**allele**)
### Terminology

| PC  | Variable [x]   | Value [3.14] |
| --- | -------------- | ------------ |
| BIO | Gene   [color] | allele [red] |

### Example: Represent integers as binary code

![[int_binary_mapping_img.png]]
In order to find the global optimum, every feasible solution must be represented in genotype space.

### Two sides of representation
- Given some space of phenotypes, i.e., entities that can be solutions to our problem a representation is: 
	- The **genotype space** (where to map phenotypes) 
	- The **mapping** (how is this done)
 
- The term “representation” is often used only for the genotype space, e.g. “binary representation”
- This can be specific enough (if we use some standard or otherwise straightforward mapping for that space), or 
- not (if we use some specific mapping into the same space)

### Representation (dis)continuity
**Example:**
- **Phenotypes**: positive integers
- **Genotypes**: binary strings
- **Mapping**: the usual binary representation of integers
- **Problem**: phenotypic distance between 7 and 8 is small, but the genotypic distance is big
- **Solution**: other mapping, for instance Gray code, a.k.a. reflected binary code

### Strong causality principle
- Small alterations in the underlying structure of an object cause small changes in the object’s behavior.
- **Small** **change** to the **cause** —> **small** **change** of the **effect**.
- Without this principle no continuity would be ensured in the evolutionary process
- Studied in [[evolution strategies]] and [[genetic programming]], e.g., Bäck and Schwefel (1993), Rosca and Ballard (1995), but crucial in EC in general

### Good representations 
- Small changes to a genotype induce small changes in the corresponding phenotypes
	- Lack of this causes discontinuities 
- Searchability!

### Popular Representation Types #TODO 
- [[Binary Representation]]
- [[Permutation Representations]]
- [[Tree Representation]]