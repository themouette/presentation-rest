# HTTP and REST

---

# Disclaimer

You already know about all of this, but this might be a new way to look at it...

---

# It's all about resources

Everything is a **resource**:

* identified by its **URI**
* with several different **representations**

> A **<accronym title="Unique Resource Location">URL</accronym>** is a
> **<accronym title="Unique Resource Identifier">URI</accronym>** but there is
> others.

---

# URI

It's the **resource**'s reference address, where to contact it.

It is **unique** for each resource.

For instance, considering **YOU** being a resource, your **URI** would be your
**post address**.

> A resource can have other non reference locations, and this reference can
> change depending on the client.
> You have personal and professional emails, phone numbers...

---

# Representations

Say you want a **Billie Holiday** album, you can get it:

* as files (mp3, flac, ogg...)
* CD
* vinyl record
* tape

It's always the same **resource** with different representations!

---

# Interacting

To interact with a resource, we use verbs.

    PLAY "Billie Holiday's album"
    LIGHT "candle"
    GET "wine"
    PUR "wine"
    SERVE "diner"
    OFFER "roses"
    GET "sex"

> It should sound natural, that's the key of a good API.

---

# Organize

Resources can be organized into collections:

* `albums` are identified by band + title
* `candles` are identified by location
* `people` are identified by name

Each collection may have relations

* `people` can have `albums` and `candles`
* `albums` have `owners` and `artist`
