# Kimball Dimentional Modeling

## Data Capture vs Data Analysis
two purposes of info asset
- operational record keeping -> operational system -> data in -> data capture
  - deal with one transaction record at a time
- analytical decision making -> DW/BI system -> data out -> data analysis
  - deal with hundreds of thousands of transaction once

## Goals of DW/BI
1. easily accessible
2. consistent ->  assembled from a variety of sources, cleansed, quality assured
3. adapt to change
4. timely
5. secure
6. support for decision making
7. acceptable by business community -> behave like you're a hybrid DBA/MBA

## Dimensional Modeling
- deliver data that's understandable to business users
- deliver fast query performance

Dimensional Modeling vs third norm form (3NF/entity-relationship model)
- 3NF seek to remove data redundancies while dimensional model make database simple
- 3NF is useful in operational processing while too complicated for BI queries (most relational database management systems cannot efficiently query a normalized model)

Star Schema vs. OLAP cubes
- star schema: Dimensional models implemented in relational database management systems are referred to as
- online analytical processing (OLAP) cubes: Dimensional models implemented in multidimensional database environments
  - pros: cubes deliver superior query performance because of the precalculations, indexing strategies, and other optimizations. Business users can drill down or up by adding or removing attributes from their analyses with excellent 
performance without issuing new queries.
  - cons: The downside is that you pay a load performance price for these capabilities, especially with large data sets.

Considerations:
- A star schema hosted in a relational database is a good physical foundation for building an OLAP cube
- OLAP has extreme performance advantages over RDBMS but requires more on computer hardware
- OLAP cubes off er signifi cantly richer analysis capabilities than RDBMSs
- OLAP cubes gracefully support slowly changing dimension type 2 changes
