Common OQL statements to query objects in java heap, on Eclipse MAT. These queries are collected from my daily usage, or somebody's blogs, books, etc.
===
1. show all instances of `java.lang.String`.
```sql
select * from java.lang.String
```
---
2. show all `java.lang.String` instances whose length is larger than 256.
```sql
select * from java.lang.String s where s.count > 256
```
---
3. show all `java.lang.ref.Reference` objects, including objects of subclass of `java.lang.ref.Reference`.
```sql
select * from instanceof java.lang.ref.Reference
```
---
4. show int array that have 256 or more elements.
```sql
select * from [I a where a.length >= 256
```
---
5. show name of all classloader class.
```sql 
select * from classof(cl).name from instanceof java.lang.ClassLoader cl
```
6. show objects referred by a soft reference.
```sql
select ref.reference from java.lang.ref.SoftReference ref 
where ref.reference != null
```
7. show referents that are not referred by another object. i.e., the referent is reachable only by that soft reference. 
```sql
select f.referent from java.lang.ref.SoftReference f 
where f.referent != null && referrers(f.referent).length == 1
```