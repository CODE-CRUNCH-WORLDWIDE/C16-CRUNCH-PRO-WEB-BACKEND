# Week 2 — Quiz

Ten questions. Lectures closed.

---

**Q1.** A `CharField` and a `TextField` differ in that:

- A) `CharField` is faster to query.
- B) `CharField` requires `max_length`; `TextField` does not.
- C) `TextField` can store binary data; `CharField` cannot.
- D) `CharField` is encrypted by default.

<details>
<summary>Answer</summary>

**B** — `CharField` requires `max_length`. (It's also slightly different in SQL — varchar(N) vs TEXT — but the *requirement* is the discriminator.)

</details>

---

**Q2.** For currency values, you should use:

- A) `FloatField`.
- B) `DecimalField` with `max_digits` and `decimal_places`.
- C) `IntegerField` storing cents.
- D) Either B or C are defensible; never A.

<details>
<summary>Answer</summary>

**D** — `DecimalField` is the textbook answer; `IntegerField` storing cents is also defensible and avoids floating-point issues entirely. Never `FloatField`.

</details>

---

**Q3.** `on_delete=CASCADE` on a `ForeignKey` means:

- A) Refuse to delete the parent if children exist.
- B) Delete this row when the referenced row is deleted.
- C) Set this row's FK to NULL.
- D) Bypass Django entirely.

<details>
<summary>Answer</summary>

**B** — Delete this row.

</details>

---

**Q4.** Iterating `Article.objects.all()` and accessing `article.author.name` for each issues how many SQL queries by default? (assume 100 articles)

- A) 1
- B) 2
- C) 100
- D) 101

<details>
<summary>Answer</summary>

**D** — 1 query to fetch articles + 100 to fetch each author = 101.

</details>

---

**Q5.** Which method should you reach for FIRST when you see N+1 on a `ForeignKey`?

- A) `prefetch_related`
- B) `select_related`
- C) `defer`
- D) `only`

<details>
<summary>Answer</summary>

**B** — `select_related` for FKs and one-to-ones; `prefetch_related` for M2M and reverse FKs.

</details>

---

**Q6.** `default=timezone.now()` (with parentheses) on a `DateTimeField` causes:

- A) Every new row to get the current time at save.
- B) Every new row to get the same fixed time — whenever Django imported the model.
- C) An exception at migration time.
- D) A warning but otherwise works.

<details>
<summary>Answer</summary>

**B** — `timezone.now()` evaluates ONCE at class-definition time. Pass `timezone.now` (callable) instead.

</details>

---

**Q7.** A migration file's `dependencies` list specifies:

- A) The migrations that must already be applied before this one runs.
- B) Other Python packages required.
- C) The Django version required.
- D) The migrations that depend on this one.

<details>
<summary>Answer</summary>

**A** — Dependencies must already be applied first.

</details>

---

**Q8.** Without `__str__`, the Django admin shows each row as:

- A) The model's primary key.
- B) "(no string representation)"
- C) "Article object (1)" — i.e., class name + ID.
- D) The first text field on the model.

<details>
<summary>Answer</summary>

**C** — "Article object (1)" — the default `__repr__`-ish format.

</details>

---

**Q9.** `ModelAdmin.list_filter` adds:

- A) A search box at the top of the list view.
- B) Sidebar filter dropdowns on the list view.
- C) A second sort option.
- D) Bulk action buttons.

<details>
<summary>Answer</summary>

**B** — Sidebar filter dropdowns.

</details>

---

**Q10.** You set `related_name="articles"` on `Article.author = ForeignKey(User, ...)`. How do you get all articles for a user?

- A) `user.article_set.all()`
- B) `user.articles.all()`
- C) `Article.objects.filter(author=user)`
- D) Either B or C.

<details>
<summary>Answer</summary>

**D** — Both work. `user.articles.all()` is more idiomatic.

</details>

If 9+: ship the homework. 7-8: re-read the relevant lecture. <7: re-read Lecture 1 from the top.

---
