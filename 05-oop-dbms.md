# SECTION 9 — OOP (20 Questions)

### Q1. Which statement best describes ENCAPSULATION?

A. Binding data and the methods that operate on it together, hiding internal state behind an interface

B. Inheriting members from a parent class

C. Defining several methods with the same name

D. Representing only essential features while ignoring details

**Correct Answer:** A

**Difficulty:** Easy

**Topic:** Encapsulation

**Explanation:**
Encapsulation bundles state with behaviour and exposes it through public methods (often with private fields). Inheritance, overloading, and abstraction are separate concepts.

**Why the other options are wrong:**
- B: That is inheritance.
- C: That is overloading.
- D: That is abstraction.

**Key Concept:** Encapsulation = bundle data + behaviour, hide internals.

---

### Q2. What is an OBJECT in OOP?

A. A blueprint that defines attributes and behaviours

B. A built-in library

C. A runtime instance of a class, with its own state

D. A collection of static methods

**Correct Answer:** C

**Difficulty:** Easy

**Topic:** Classes and Objects

**Explanation:**
The class is the blueprint; an object is an instance created from it at runtime, each holding its own state. Libraries and static collections are not object instances.

**Why the other options are wrong:**
- A: That is the class.
- B: That is a library/package.
- D: Static utility classes exist but aren't the definition.

**Key Concept:** Class = blueprint; object = instance.

---

### Q3. WHEN is a constructor invoked?

A. When the program compiles

B. When an object of the class is created (via new / instantiation)

C. When a method is called on an object

D. When the class is imported

**Correct Answer:** B

**Difficulty:** Easy

**Topic:** Constructors

**Explanation:**
Constructors initialise a new object and run at instantiation time. Compilation, method calls, and imports do not trigger constructors.

**Why the other options are wrong:**
- A/C/D: All non-instantiation moments.

**Key Concept:** Constructor runs when you create an object.

---

### Q4. In Java, which mechanism allows a class to inherit behaviour from MULTIPLE types?

A. Extending multiple classes

B. Extending one class and nothing else

C. Anonymous classes only

D. Implementing multiple interfaces

**Correct Answer:** D

**Difficulty:** Easy

**Topic:** Multiple Inheritance

**Explanation:**
Java classes can extend only one superclass, but can implement many interfaces, achieving a safe form of multiple inheritance (no diamond ambiguity on state).

**Why the other options are wrong:**
- A: Java forbids multiple class inheritance.
- B: Only single inheritance.
- C: Anonymous classes don't add multiple inheritance.

**Key Concept:** Interfaces give Java multiple-inheritance-like flexibility.

---

### Q5. Method OVERLOADING is resolved at which time?

A. Compile time — the compiler picks the method by argument signature

B. Runtime — the JVM picks it dynamically

C. Load time — when the class is loaded

D. It is never resolved

**Correct Answer:** A

**Difficulty:** Moderate

**Topic:** Method Overloading

**Explanation:**
Overloading (same name, different parameter list) is decided statically by the compiler based on argument types. This is compile-time (static) polymorphism.

**Why the other options are wrong:**
- B: Runtime dispatch is overriding (dynamic polymorphism).
- C/D: Irrelevant phases.

**Key Concept:** Overloading = compile-time; overriding = runtime.

---

### Q6. Method OVERRIDING enables which kind of polymorphism?

A. Static polymorphism

B. Parameter overloading

C. Runtime (dynamic) polymorphism — the subclass's version is chosen by the actual object type at runtime

D. Generics-based polymorphism

**Correct Answer:** C

**Difficulty:** Moderate

**Topic:** Method Overriding / Polymorphism

**Explanation:**
When a subclass redefines an inherited method, the JVM dispatches to the method of the actual runtime object type — the essence of dynamic binding.

**Why the other options are wrong:**
- A: That is overloading.
- B/D: Unrelated mechanisms.

**Key Concept:** Overriding → runtime/dynamic dispatch.

---

### Q7. A developer says: "The user calls bankAccount.withdraw(100) without needing to know whether the backend merges accounts or charges fees." Which OOP concept does this illustrate?

A. Encapsulation

B. Abstraction — using the essential interface while hiding implementation details

C. Is-a inheritance

D. Method overloading

**Correct Answer:** B

**Difficulty:** Moderate

**Topic:** Abstraction — Identification

**Explanation:**
Abstraction exposes a clean interface (withdraw) hiding how the operation works internally. This is about hiding implementation complexity, not about bundling data or hierarchy.

**Why the other options are wrong:**
- A: Encapsulation specifically hides state via access control.
- C: No class hierarchy mentioned.
- D: One method call, no overloads.

**Key Concept:** Keyboard abstraction: interface visible, internals hidden.

---

### Q8. Given the code, what is the problem?

```
class Account {
    private double balance;
}
public static void main(...) {
    Account a = new Account();
    a.balance = 1000;
}
```

A. Nothing — balance is accessible

B. balance should be protected

C. The class needs more private fields

D. balance is private, so external code cannot access it directly — a compile error (encapsulation violation)

**Correct Answer:** D

**Difficulty:** Moderate

**Topic:** Encapsulation — Code Analysis

**Explanation:**
`private` restricts access to within the class. Direct assignment from outside fails to compile; proper access needs a public method like `setBalance`.

**Why the other options are wrong:**
- A: Private members are hidden.
- B: Would still not permit direct outside assignment.
- C: Number of fields is irrelevant.

**Key Concept:** private = class-only; outsiders need public accessors.

---

### Q9. What does the following code print?

```
class Animal { void sound() { println("generic"); } }
class Dog extends Animal { void sound() { println("bark"); } }

Animal a = new Dog();
a.sound();
```

A. bark

B. generic

C. compile error

D. dog

**Correct Answer:** A

**Difficulty:** Moderate

**Topic:** Runtime Polymorphism — Code Trace

**Explanation:**
The reference type is Animal, but the object is a Dog. Overridden methods dispatch to the actual runtime type, so Dog's sound() prints "bark".

**Why the other options are wrong:**
- B: Would hold only if sound() were not overridden or the reference's type decided.
- C: This is legal (upcasting).
- D: Not a printed string.

**Key Concept:** Reference type ≠ runtime type; overriding follows the object.

---

### Q10. In a class hierarchy, the derived-class constructor implicitly starts by calling:

A. Its own first line of code

B. The superclass constructor (super(), implicit if not written)

C. Object's constructor even when the direct parent has one — the chain reaches Object transitively

D. The default constructor of the most derived sibling

**Correct Answer:** B

**Difficulty:** Moderate

**Topic:** Constructor Chaining

**Explanation:**
If not written, `super()` is inserted as the first statement, initialising the parent chain before the child's body runs. Object's constructor is reached eventually, but the implicit first call is to the direct parent.

**Why the other options are wrong:**
- A: The child body runs after the parent chain.
- C: Object's constructor runs transitively, but not as the direct implicit target.
- D: No sibling calls.

**Key Concept:** Constructors chain via implicit super().

---

### Q11. Why can you NOT override a method marked `final` in a superclass?

A. final methods are very fast, so overriding is disallowed for speed

B. final means the method was removed

C. final marks it as immutable in behaviour — subclasses are forbidden from replacing it (design: no extension points)

D. final is only about variables

**Correct Answer:** C

**Difficulty:** Moderate

**Topic:** final Method

**Explanation:**
`final` on a method declares it unchangeable: the author deliberately closes the extension seam to preserve invariant behaviour. It is a design decision, not a speed/keyword-context matter.

**Why the other options are wrong:**
- A: Not a performance feature.
- B: Method still exists.
- D: final applies to methods, classes, and variables.

**Key Concept:** final methods cannot be overridden.

---

### Q12. "A Car HAS-A Engine; a Car IS-A Vehicle." Which terms describe these relationships correctly?

A. Both are inheritance

B. Both are composition

C. HAS-A is inheritance; IS-A is composition

D. HAS-A is composition/aggregation; IS-A is inheritance

**Correct Answer:** D

**Difficulty:** Moderate

**Topic:** Is-a vs Has-a

**Explanation:**
IS-A (Car extends/implements Vehicle) is inheritance. HAS-A (Car contains Engine) is composition/aggregation — a relationship of ownership, not of typing.

**Why the other options are wrong:**
- A/B: Mix up the two relationships.
- C: Reverses both.

**Key Concept:** IS-A→inheritance; HAS-A→composition.

---

### Q13. Class B (in package Y) extends class A (in package X). Member m of A is `protected`. Which statement is TRUE?

A. B can access m, and any other class in package Y can too (protected includes package access)

B. Only A can access m

C. No other class can ever access m

D. protected means public everywhere

**Correct Answer:** A

**Difficulty:** Hard

**Topic:** Access Modifiers Across Packages

**Explanation:**
`protected` grants access to the same package AND any subclass (even in another package). So B (subclass across packages) can access m, as can other package-Y classes.

**Why the other options are wrong:**
- B: A's own members are always accessible anyway; the interesting part is B.
- C: Contradicts protected semantics.
- D: protected is not public.

**Key Concept:** protected = package access + subclass access.

---

### Q14. Two Java interfaces both declare a default method with the SAME signature, and a class implements both. What must the class do?

A. It compiles automatically with no action

B. It must override the conflicting default method (or the code won't compile) — this is the "diamond problem" for interfaces

C. It must delete one interface

D. It can pick the winner by priority of import order

**Correct Answer:** B

**Difficulty:** Hard

**Topic:** Diamond Problem

**Explanation:**
When two defaults collide, the class faces ambiguity and the compiler demands an explicit override resolving which default (or new behaviour) to use. Import order does not decide.

**Why the other options are wrong:**
- A: Conflicting defaults cause a compile error without resolution.
- C: No need to delete interfaces.
- D: No such ordering rule.

**Key Concept:** Conflicting interface defaults must be overridden.

---

### Q15. A class declares ONLY the constructor `Player(int score)`. Which statement is TRUE?

A. `new Player()` works fine using a hidden default constructor

B. The default no-arg constructor is added automatically alongside it

C. The no-arg default constructor disappears — `new Player()` will NOT compile

D. Constructors cannot take parameters

**Correct Answer:** C

**Difficulty:** Hard

**Topic:** Default Constructor Replacement

**Explanation:**
Defining any constructor suppresses the compiler-generated no-arg constructor. Unless you explicitly add a `Player()`, instantiating without arguments won't compile.

**Why the other options are wrong:**
- A/B: Once one constructor is declared, the default isn't auto-added.
- D: Parameterised constructors are standard.

**Key Concept:** Declare any constructor → default no-arg vanishes.

---

### Q16. Subclass D defines a static method with the SAME signature as a static method in parent P. `P.m()` called via a D reference... which statement is correct?

A. This is overriding, resolved at runtime

B. Static methods are always overloaded in subclasses

C. The child version overrides and the parent's name is erased

D. Static methods are HIDDEN, not overridden — the version used depends on the reference type, not polymorphically

**Correct Answer:** D

**Difficulty:** Hard

**Topic:** Static Method Hiding vs Overriding

**Explanation:**
Static methods are resolved by reference type, not object type; a same-signature static in the subclass 'hides' the parent's. This is hiding, distinct from dynamic overriding.

**Why the other options are wrong:**
- A: Static dispatch is not runtime polymorphism.
- B: Not overload-resolution logic.
- C: Parent's static still exists.

**Key Concept:** Static = hiding by reference type; instance = overriding by object.

---

### Q17. A method `void play(Instrument i)` is called with a Guitar object. The chosen implementation is that of Guitar even though the parameter type is Instrument. Which concept is being exercised?

A. Dynamic dispatch / runtime polymorphism

B. Compile-time method overloading

C. Operator overloading

D. Reflection

**Correct Answer:** A

**Difficulty:** Hard

**Topic:** Polymorphism — Identification

**Explanation:**
The decision of which overridden method runs happens at runtime based on the object's actual type — classic dynamic dispatch.

**Why the other options are wrong:**
- B: No multiple same-name signatures involved.
- C: No operators.
- D: No runtime introspection described.

**Key Concept:** Actual object type picks the method at runtime.

---

### Q18. You override equals() in a class but NOT hashCode(). Two equal objects return different hash codes. Which contract is violated?

A. The Comparable contract

B. The equals/hashCode contract — equal objects must have equal hash codes for hash-based collections to work

C. The constructor contract

D. The serialization contract

**Correct Answer:** B

**Difficulty:** Advanced

**Topic:** equals/hashCode Contract

**Explanation:**
Hash collections (HashMap/HashSet) first bucket by hashCode, then compare with equals. If equal objects hash differently, they land in different buckets and lookups break — so overriding only equals() is a bug.

**Why the other options are wrong:**
- A: Comparable is about ordering.
- C/D: Unrelated contracts.

**Key Concept:** Override equals() and hashCode() together, consistently.

---

### Q19. A shallow-copy constructor does `this.list = other.list;` for a member list. What risk arises when the copy mutates list?

A. None — copies are always independent

B. The copy fails to compile

C. Both objects share the same list reference — mutating one affects the other (a shared-state bug); deep copies build a new list

D. It triggers infinite recursion

**Correct Answer:** C

**Difficulty:** Advanced

**Topic:** Shallow vs Deep Copy

**Explanation:**
Shallow copy duplicates the reference, not the object it points to. Both original and copy alias one list, so mutations leak across — deep copying creates independent structures.

**Why the other options are wrong:**
- A: Shallow copies alias mutable members.
- B: It compiles fine.
- D: No recursion.

**Key Concept:** Shallow copy aliases references; deep copy duplicates objects.

---

### Q20. A team has a `Penguin` class that wants the abilities of `Bird`. Instead of making a fragile inheritance chain, they give Penguin a `Behaviour` object it delegates to. Which principle does this best illustrate?

A. Multiple class inheritance via extends

B. Global mutable state

C. Method overloading everywhere

D. Composition-over-inheritance / delegation (favour HAS-A over IS-A)

**Correct Answer:** D

**Difficulty:** Advanced

**Topic:** Composition Over Inheritance

**Explanation:**
Delegating behaviour to a composed 'Behaviours' object is composition — flexible, avoids deep brittle hierarchies (and the bird-that-can't-fly problem). It is not inheritance, globals, or overloading.

**Why the other options are wrong:**
- A: No extends chain described.
- B: No shared global state described.
- C: No same-name overloads described.

**Key Concept:** Prefer delegation/composition to rigid inheritance.

---

# SECTION 10 — DBMS & SQL (30 Questions)

Reference data for many questions below:

**Employees**

| emp_id | name | dept_id | salary | city |
|--------|------|---------|--------|------|
| 1 | Alice | 10 | 50000 | Pune |
| 2 | Bob | 10 | 45000 | Mumbai |
| 3 | Carol | NULL | 60000 | Delhi |
| 4 | Dave | 20 | 55000 | Pune |
| 5 | Eve | 20 | 62000 | Mumbai |

**Departments**

| dept_id | dname |
|---------|-------|
| 10 | IT |
| 20 | Sales |
| 30 | HR |

---

### Q1. Which two properties always hold for a PRIMARY KEY?

A. Unique AND not null

B. Nullable but unique

C. Unique but nullable is allowed

D. Can be duplicated

**Correct Answer:** A

**Difficulty:** Easy

**Topic:** Primary Key

**Explanation:**
A primary key uniquely identifies every row, so it can never be NULL and no two rows may hold the same value. Nullable or duplicate keys would break uniqueness.

**Why the other options are wrong:**
- B/C: NULLs undermine row identity.
- D: Duplication breaks the definition.

**Key Concept:** PK = unique + NOT NULL.

---

### Q2. A FOREIGN KEY in table X:

A. Must have the same name as the referenced column

B. Can reference any column in any table, guaranteed to be unique? — NO

C. References the PRIMARY KEY (or unique key) of another table, enforcing referential integrity

D. Must be part of X's composite key

**Correct Answer:** C

**Difficulty:** Easy

**Topic:** Foreign Key

**Explanation:**
A foreign key stores values that must match a referenced key (usually the parent's PK), so rows can't point at non-existent records. Column names and FKs in composite keys are not requirements.

**Why the other options are wrong:**
- A: Name matching is optional.
- B: It references a unique key, not any arbitrary column.
- D: FK placement is by design, not formula.

**Key Concept:** FK → referenced primary key; ensures integrity.

---

### Q3. What is a CANDIDATE KEY?

A. Any index created by the DBA

B. A minimal set of attributes that can uniquely identify every row (a candidate to become the primary key)

C. A key that allows NULLs

D. The clustered index of a table

**Correct Answer:** B

**Difficulty:** Easy

**Topic:** Candidate Key

**Explanation:**
A candidate key is a MINIMAL superkey — no subset of it still uniquely identifies rows. Usually one candidate is chosen as the primary key.

**Why the other options are wrong:**
- A: Indexes are implementation details, not keys.
- C: Keys by definition can't contain NULLs.
- D: Clustering is a storage choice.

**Key Concept:** Candidate key = minimal unique identifier.

---

### Q4. In SELECT, what does the WHERE clause act on?

A. Groups

B. Columns in the select list (that's projection)

C. Aggregate results

D. Individual rows before grouping

**Correct Answer:** D

**Difficulty:** Easy

**Topic:** WHERE Clause

**Explanation:**
WHERE filters rows individually before any grouping/aggregation. Groups are filtered by HAVING, and selecting columns is projection.

**Why the other options are wrong:**
- A/C: Those are HAVING's job.
- B: Projection picks columns, not filters rows.

**Key Concept:** WHERE filters rows; HAVING filters groups.

---

### Q5. What does SELECT DISTINCT accomplish?

A. Removes duplicate ROWS from the result set

B. Removes NULL values

C. Sorts the output

D. Restricts rows by a condition

**Correct Answer:** A

**Difficulty:** Easy

**Topic:** DISTINCT

**Explanation:**
DISTINCT collapses identical rows so each unique combination appears once. It does not filter by condition, sort, or drop NULLs.

**Why the other options are wrong:**
- B: It affects row duplicates, not nullness.
- C: ORDER BY sorts.
- D: WHERE filters.

**Key Concept:** DISTINCT = de-duplicate result rows.

---

### Q6. Which of these situations VIOLATES 1NF?

A. A column that never contains NULLs

B. A primary key constraint present

C. A single column storing multiple values separated by commas (a repeating group)

D. A numeric column with negative values

**Correct Answer:** C

**Difficulty:** Easy

**Topic:** 1NF

**Explanation:**
1NF demands atomic (single, indivisible) values and no repeating groups. A comma-separated list in one column breaks atomicity and must be split into a related table.

**Why the other options are wrong:**
- A/B/D: All legal in 1NF.

**Key Concept:** 1NF = atomic values, no comma-packed columns.

---

### Q7. A table with a COMPOSITE primary key (A, B) has a non-key column depending on only A (part of the key). Which form is violated?

A. 1NF

B. 2NF — no PARTIAL dependencies on part of a composite key

C. 3NF

D. BCNF automatically, but the primary violation is 3NF

**Correct Answer:** B

**Difficulty:** Moderate

**Topic:** 2NF

**Explanation:**
If a non-key attribute depends on only part of the composite key, that's a partial dependency — the specific breach 2NF prohibits. 3NF deals with transitive (non-key to non-key) dependencies.

**Why the other options are wrong:**
- A: Atomicity presumably holds.
- C/D: Concern non-key-to-non-key dependencies.

**Key Concept:** 2NF bans partial dependencies on any part of the key.

---

### Q8. A table satisfies 2NF. Which dependency must ALSO be eliminated to reach 3NF?

A. Partial dependency on the key

B. Any functional dependency at all

C. A key dependency

D. A transitive dependency — a non-key column depending on another non-key column

**Correct Answer:** D

**Difficulty:** Moderate

**Topic:** 3NF

**Explanation:**
3NF = 2NF + no transitive dependencies: non-key columns must depend only on the key, not on other non-key columns. Partial dependencies are already gone at 2NF.

**Why the other options are wrong:**
- A: Already handled by 2NF.
- B/C: A dependency on the full key is exactly what's allowed.

**Key Concept:** 3NF = no non-key → non-key dependencies.

---

### Q9. `SELECT dept_id, COUNT(*) FROM Employees GROUP BY dept_id;` — which result set is correct?

A. (10, 2), (20, 2), (NULL, 1)

B. (10, 2), (20, 2)

C. (10, 4)

D. Error, because dept_id contains NULL

**Correct Answer:** A

**Difficulty:** Moderate

**Topic:** GROUP BY Output

**Explanation:**
Grouping creates one row per distinct dept_id: 10→Alice+Bob=2, 20→Dave+Eve=2, and NULL forms its own group (Carol)=1. NULL does not cause an error.

**Why the other options are wrong:**
- B: Drops the NULL group.
- C: 4 is wrong grouping arithmetic.
- D: NULLs group normally in GROUP BY.

**Key Concept:** GROUP BY includes a separate NULL group.

---

### Q10. Which clause filters GROUPS (after aggregation) rather than individual rows?

A. WHERE

B. LIMIT

C. HAVING

D. GROUP BY itself

**Correct Answer:** C

**Difficulty:** Moderate

**Topic:** WHERE vs HAVING

**Explanation:**
HAVING evaluates conditions on grouped/aggregated values (e.g., COUNT(*) > 2). WHERE must run before grouping and cannot reference aggregates.

**Why the other options are wrong:**
- A: Row-level filter, pre-aggregation.
- B: Row-count limiter.
- D: GROUP BY groups; it does not filter.

**Key Concept:** HAVING = aggregate filter; WHERE = row filter.

---

### Q11. How many rows does `SELECT * FROM Employees INNER JOIN Departments ON Employees.dept_id = Departments.dept_id;` return?

A. 3

B. 4

C. 5

D. 6

**Correct Answer:** B

**Difficulty:** Moderate

**Topic:** INNER JOIN

**Explanation:**
Matching dept_id 10 pairs Alice/Bob with IT (2 rows) and 20 pairs Dave/Eve with Sales (2 rows). Carol's NULL matches nothing, and HR (30) has no employees, so 2+2 = 4 rows.

**Why the other options are wrong:**
- A: 3 miscounts matches.
- C: Includes Carol — but INNER JOIN drops unmatched rows.
- D: 5×1 + 1.

**Key Concept:** INNER JOIN keeps only rows with matches on both sides.

---

### Q12. How many rows does `SELECT * FROM Employees LEFT JOIN Departments ON Employees.dept_id = Departments.dept_id;` return?

A. 4

B. 3

C. 6

D. 5 — every employee stays, even Carol with no matching department (NULL in the dname column)

**Correct Answer:** D

**Difficulty:** Moderate

**Topic:** LEFT JOIN

**Explanation:**
LEFT (outer) JOIN preserves every row from the left table, filling unmatched right-side columns with NULL. Employees has 5 rows, so 5 result rows (4 matched + Carol with NULL).

**Why the other options are wrong:**
- A: That's the inner-join count.
- B: Too few.
- C: Wrong multiplication.

**Key Concept:** LEFT JOIN = all left rows, NULLs where no match.

---

### Q13. `SELECT SUM(salary) FROM Employees WHERE city = 'Mumbai';` — what is the result?

A. 107000

B. 95000

C. 50000

D. 62000

**Correct Answer:** A

**Difficulty:** Moderate

**Topic:** SUM + WHERE

**Explanation:**
Mumbai employees are Bob (45000) and Eve (62000). Sum = 45000 + 62000 = 107000.

**Why the other options are wrong:**
- B: Left out one Mumbai salary.
- C/D: Single salaries, not the sum.

**Key Concept:** Sum aggregates only rows that pass WHERE.

---

### Q14. Consider `COUNT(*)` versus `COUNT(dname)` on Employees:

A. Both return 5

B. COUNT(*) returns 4; COUNT(dname) returns 5

C. COUNT(*) returns 5; COUNT(dname) returns 4, because Carol's unmatched row (LEFT JOIN) has a NULL dname and column COUNTs skip NULLs

D. COUNT(*) errors with a join

**Correct Answer:** C

**Difficulty:** Moderate

**Topic:** COUNT(*) vs COUNT(column)

**Explanation:**
COUNT(*) counts all rows (5). COUNT(column) ignores NULLs — after the LEFT JOIN, one row's dname is NULL, so it counts 4. This NULL-sensitivity is the classic COUNT trap.

**Why the other options are wrong:**
- A: Column counts drop NULLs.
- B: Numbers are reversed.
- D: Counting works fine.

**Key Concept:** COUNT(col) skips NULLs; COUNT(*) never does.

---

### Q15. `SELECT name FROM Employees WHERE dept_id = NULL;` returns:

A. Carol

B. No rows — NULL can never satisfy `= NULL`; you need `IS NULL`

C. Every employee

D. A runtime crash

**Correct Answer:** B

**Difficulty:** Moderate

**Topic:** NULL Semantics

**Explanation:**
In SQL, NULL comparisons yield UNKNOWN, so `= NULL` never matches — even a genuine NULL column value. The correct filter is `dept_id IS NULL`.

**Why the other options are wrong:**
- A: `IS NULL` would find Carol; `=` does not.
- C: The condition is never true.
- D: It's not an error, just empty.

**Key Concept:** NULL needs IS NULL / IS NOT NULL.

---

### Q16. Which ACID property ensures that two concurrent transactions do not interfere with each other's intermediate state?

A. Atomicity

B. Consistency

C. Durability

D. Isolation

**Correct Answer:** D

**Difficulty:** Moderate

**Topic:** ACID — Isolation

**Explanation:**
Isolation keeps concurrent transactions from seeing each other's uncommitted/partial changes (different isolation levels trade strictness for concurrency). Atomicity = all-or-nothing; consistency = valid state; durability = survives crashes.

**Why the other options are wrong:**
- A: All-or-nothing execution.
- B: Referential/rule validity.
- C: Persistence after commit.

**Key Concept:** Isolation = transactions don't disturb one another.

---

### Q17. After a lengthy transaction, the application executes COMMIT. What is the effect?

A. All changes in the transaction are made permanent and visible to other transactions

B. All changes are discarded

C. The transaction restarts

D. The database is closed

**Correct Answer:** A

**Difficulty:** Moderate

**Topic:** Transactions — Commit

**Explanation:**
COMMIT makes the transaction's changes durable and publicly visible. ROLLBACK (the alternative) undoes them; neither restarts nor shuts the database.

**Why the other options are wrong:**
- B: That's ROLLBACK.
- C/D: No restart/close semantics.

**Key Concept:** COMMIT = make it permanent; ROLLBACK = undo it.

---

### Q18. Which statement about DELETE, TRUNCATE, and DROP is correct?

A. They are identical in effect

B. TRUNCATE can remove specific rows with WHERE

C. DELETE can remove specific rows (WHERE), TRUNCATE quickly clears all rows but keeps structure, DROP removes the entire table

D. DROP only removes rows, not structure

**Correct Answer:** C

**Difficulty:** Hard

**Topic:** DELETE vs TRUNCATE vs DROP

**Explanation:**
DELETE is DML and supports WHERE (row-level, logged). TRUNCATE is DDL — fast, no WHERE, removes all rows, keeps the table. DROP is DDL that removes the table and its definition entirely.

**Why the other options are wrong:**
- A: Different semantics and recovery behaviour.
- B: TRUNCATE cannot filter.
- D: DROP removes everything.

**Key Concept:** DELETE=rows+WHERE; TRUNCATE=all rows, no filter; DROP=whole table.

---

### Q19. Why does `SELECT name, salary FROM Employees GROUP BY dept_id;` fail in most databases?

A. GROUP BY requires an aggregate in every query

B. name and salary are neither grouped columns nor aggregate functions — they have multiple values per group

C. dept_id is not selected

D. GROUP BY cannot be used with SELECT

**Correct Answer:** B

**Difficulty:** Hard

**Topic:** GROUP BY Rule

**Explanation:**
After grouping by dept_id, each group holds several names/salaries, so selecting a bare name/salary is ambiguous. Only grouped columns (like dept_id) and aggregates are allowed.

**Why the other options are wrong:**
- A: Grouping doesn't require aggregates everywhere.
- C: It can be omitted from the select.
- D: GROUP BY is standard in SELECT.

**Key Concept:** Group by column ⇒ select only grouped/aggregated columns.

---

### Q20. You join Employees to Departments on dept_id. dept_id is the PK of Departments but not unique in Employees. What can happen to the result row count?

A. Never exceeds the smaller table

B. Always equals the larger table

C. A non-unique join key can cause rows to multiply (each matching pair) — typically harmless when key is unique on the 'one' side if the FK is intended as many-to-one

D. Preserves exactly 1 row per employee regardless of matches

**Correct Answer:** C

**Difficulty:** Hard

**Topic:** Join Semantics / Duplicate Keys

**Explanation:**
A join produces a Cartesian product of matching rows. If the 'many' side has duplicates of the key, each duplicate pairs with the single parent row, multiplying rows — which is often a logic bug.

**Why the other options are wrong:**
- A/B/D: Are not guaranteed behaviours; row count follows matching pairs.

**Key Concept:** Join row count = matches × matches.

---

### Q21. What does this self-join return?

```
SELECT e2.name
FROM Employees e1 JOIN Employees e2
  ON e1.dept_id = e2.dept_id AND e1.emp_id <> e2.emp_id
WHERE e1.name = 'Alice';
```

A. Bob — Alice's colleagues within dept 10, excluding Alice herself

B. Alice

C. All five employees

D. Dave and Eve

**Correct Answer:** A

**Difficulty:** Hard

**Topic:** Self-Join

**Explanation:**
The join pairs each employee with same-dept, different-id employees. Alice's pair is Bob (dept 10), so e2.name = Bob. Alice is excluded by emp_id inequality.

**Why the other options are wrong:**
- B: The `<>` excludes Alice.
- C/D: Wrong departments/filters.

**Key Concept:** Self-join finds related rows within one table.

---

### Q22. `SELECT name FROM Employees ORDER BY salary DESC LIMIT 3;` returns which names?

A. Alice, Dave, Eve

B. Eve, Carol, Dave

C. Dave, Bob, Alice

D. Carol, Eve, Dave

**Correct Answer:** B

**Difficulty:** Hard

**Topic:** ORDER BY + LIMIT

**Explanation:**
Salaries desc: Eve 62000, Carol 60000, Dave 55000, Alice 50000, Bob 45000. Top 3: Eve, Carol, Dave.

**Why the other options are wrong:**
- A: That's a low-to-mid grouping.
- C: Ascending subset.
- D: Same set, wrong order.

**Key Concept:** Sort descending, keep top N.

---

### Q23. `SELECT city, COUNT(*) FROM Employees GROUP BY city HAVING COUNT(*) > 1;`

A. Pune, Delhi

B. Pune (2), Mumbai (2)

C. Delhi (1)

D. An error because HAVING can't use COUNT

**Correct Answer:** B

**Difficulty:** Hard

**Topic:** HAVING with Aggregates

**Explanation:**
Groups: Pune 2, Mumbai 2, Delhi 1. HAVING COUNT(*) > 1 keeps only Pune and Mumbai. Delhi's single row is filtered out.

**Why the other options are wrong:**
- A: Delhi has only 1, excluded.
- C: That's the excluded group.
- D: HAVING is exactly where aggregates are allowed.

**Key Concept:** HAVING works on grouped aggregate values.

---

### Q24. `SELECT name FROM Employees e1 WHERE salary > (SELECT AVG(salary) FROM Employees e2 WHERE e2.dept_id = e1.dept_id);` — which employees are returned?

A. Alice, Bob, Dave, Eve

B. Only Alice

C. Carol

D. Alice and Eve — those above their own department's average

**Correct Answer:** D

**Difficulty:** Hard

**Topic:** Correlated Subquery

**Explanation:**
For each employee the inner query computes their dept's average: dept10 avg=(50000+45000)/2=47500 → Alice (50000) qualifies, Bob (45000) not; dept20 avg=58500 → Eve (62000) qualifies, Dave (55000) not. Carol has NULL dept, excluded.

**Why the other options are wrong:**
- A: Includes those below the dept average.
- B: Misses Eve.
- C: Carol's subquery can't relate a NULL dept.

**Key Concept:** Correlated subquery re-computes per outer row.

---

### Q25. `SELECT city, AVG(salary) FROM Employees WHERE dept_id IS NOT NULL GROUP BY city HAVING AVG(salary) > 50000;`

A. Pune 52500, Mumbai 53500

B. Only Mumbai 53500

C. Pune 50000, Delhi 60000

D. No rows

**Correct Answer:** A

**Difficulty:** Hard

**Topic:** WHERE + GROUP BY + HAVING Combination

**Explanation:**
WHERE removes Carol (NULL dept). Groups: Pune avg (50000+55000)/2=52500, Mumbai avg=53500. Both exceed 50000 → two rows. (Note: operators—the averages are computed on the AVG of salaries, both > threshold.)

**Why the other options are wrong:**
- B: Pune also passes.
- C: Wrong average values.
- D: Values clearly exist.

**Key Concept:** WHERE → GROUP → HAVING, in that order.

---

### Q26. Consider `Student_Course(StudentID, CourseID, StudentName, CourseName, Grade)` with PK (StudentID, CourseID). Which form is VIOLATED?

A. 1NF, because grades repeat

B. 3NF because of transitive dependency

C. 2NF — StudentName depends only on StudentID and CourseName only on CourseID (partial dependencies)

D. No form is violated

**Correct Answer:** C

**Difficulty:** Advanced

**Topic:** Normalization — Identifying 2NF Violation

**Explanation:**
The composite key has partial dependencies: StudentName is determined by StudentID alone (not the full key) and CourseName by CourseID alone. Splitting into Student, Course, and Enrolment resolves it.

**Why the other options are wrong:**
- A: Attributes are atomic here.
- B: The violation appears at 2NF first.
- D: It is clearly violated.

**Key Concept:** Spot the non-key attribute depending on part of the composite key.

---

### Q27. `Employee(emp_id, emp_name, dept_id, dept_name)` where dept_name depends on dept_id. Which form is violated, assuming emp_id is the PK and the table is in 2NF?

A. 1NF

B. 3NF — dept_name depends transitively on emp_id via dept_id

C. No violation — this is fully normalized

D. 2NF, because the PK is composite

**Correct Answer:** B

**Difficulty:** Advanced

**Topic:** Normalization — 3NF Violation

**Explanation:**
dept_name is a non-key attribute determined by another non-key attribute (dept_id), i.e., a transitive dependency → 3NF broken. Fix: separate Department(dept_id, dept_name).

**Why the other options are wrong:**
- A: Atomicity is fine.
- C: Transitive dependency exists.
- D: Single-column PK — no partial dependency to violate 2NF.

**Key Concept:** Non-key → non-key = transitive = 3NF breach.

---

### Q28. `SELECT dept_id, MAX(salary) FROM Employees WHERE dept_id IS NOT NULL GROUP BY dept_id HAVING MAX(salary) > 60000;`

A. (10, 50000)

B. (20, 55000)

C. (10, 50000), (20, 62000)

D. (20, 62000)

**Correct Answer:** D

**Difficulty:** Advanced

**Topic:** Aggregation Pipeline

**Explanation:**
Groups: dept10 MAX=50000, dept20 MAX=62000. HAVING > 60000 keeps only dept20 with MAX=62000. Depar10's 50000 fails the group filter.

**Why the other options are wrong:**
- A: A group that fails HAVING.
- B: Not the MAX of dept20.
- C: Includes the failing group.

**Key Concept:** HAVING filters groups after MAX computed.

---

### Q29. A subquery may return MULTIPLE values. Which operator should replace the one in `WHERE col = (SELECT ...)` to accept them?

A. IN

B. LIKE

C. LIMIT

D. IS NULL

**Correct Answer:** A

**Difficulty:** Advanced

**Topic:** Subquery Operators

**Explanation:**
When a subquery yields a list, membership is tested with IN (`col IN (SELECT ...)`). `=` expects a scalar result and would error with multiple rows.

**Why the other options are wrong:**
- B: Pattern matching, unrelated.
- C: Row limiting, unrelated.
- D: NULL test, unrelated.

**Key Concept:** Multi-row subqueries use IN (or EXISTS).

---

### Q30. Two transactions run together; one reads a row whose update by the other is NOT yet committed, then the other rolls back. Why is the first transaction at risk?

A. Durability failure

B. Normal — nothing needs protection

C. It read uncommitted data (a dirty read); the rollback destroys what it based its work on — avoided with READ COMMITTED or higher isolation

D. The rollback is impossible by design

**Correct Answer:** C

**Difficulty:** Advanced

**Topic:** Isolation Levels / Dirty Reads

**Explanation:**
Reading an uncommitted update that later rolls back is a dirty read — the read was based on phantom value. READ COMMITTED isolation prevents a transaction from reading uncommitted changes.

**Why the other options are wrong:**
- A: Durability concerns committed data.
- B: This is a genuine anomaly.
- D: Rollbacks are both legal and common.

**Key Concept:** Isolation levels trade strictness vs concurrency to block anomalies.