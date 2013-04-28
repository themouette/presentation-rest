# HTTP and REST

---

# Disclaimer

You already know about all of this, but this might be a new way to look at it...

---

# It's all about resources

Everything is a **resource**:

* identified by it's **URI**
* with several **representations**

> **<accronym title="Unique Resource Location">URL</accronym>** is a **<accronym
> title="Unique Resource Identifier">URI</accronym>** but there is others.

---

# URI

It's the **resource**'s reference adress, where to contact it.

For instance, your **URI** as a resource can be your post adress.

It is **unique** for each resource.

> A resource can have other non reference locations, and this reference can
> change depending of the client.
> You have personal and professional e-mail, phone number...

---

# Representations

Say you want a **Billie Holiday** album, you can get it:

* as files (mp3, flac, ogg...)
* CD
* vinyl record
* tape

It's all the same **resource** with different representations !

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

* `albums` can are identified by band + title
* `candles` are identified by location
* `people` are identified by name

Each collection can have relations

* `people` can have `albums` and `candles`
* `albums` have `owners` and `artist`
