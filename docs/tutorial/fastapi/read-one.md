# Read One Model with FastAPI

Let's now add a *path operation* to read a single model to our **FastAPI** application.

## Path Operation for One Hero

Let's add a new *path operation* to read one single hero.

We want to get the hero based on the `id`, so we will use a **path parameter** `hero_id`.

/// info

If you need to refresh how *path parameters* work, including their data validation, check the <a href="https://fastapi.tiangolo.com/tutorial/path-params/" class="external-link" target="_blank">FastAPI docs about Path Parameters</a>.

///

{* ./docs_src/tutorial/fastapi/read_one/tutorial001_py310.py ln[1:2,59:65] hl[59] *}

For example, to get the hero with ID `2` we would send a `GET` request to:

```
/heroes/2
```

## Handling Errors

Then, because FastAPI already takes care of making sure that the `hero_id` is an actual integer, we can use it directly with `Hero.get()` to try and get one hero by that ID.

But if the integer is not the ID of any hero in the database, it will not find anything, and the variable `hero` will be `None`.

So, we check it in an `if` block, if it's `None`, we raise an `HTTPException` with a `404` status code.

And to use it, we first import `HTTPException` from `fastapi`.

This will let the client know that they probably made a mistake on their side and requested a hero that doesn't exist in the database.

{* ./docs_src/tutorial/fastapi/read_one/tutorial001_py310.py ln[1:2,59:65] hl[1,62:64] *}

## Return the Hero

Then, if the hero exists, we return it.

And because we are using the `response_model` with `HeroPublic`, it will be validated, documented, etc.

{* ./docs_src/tutorial/fastapi/read_one/tutorial001_py310.py ln[1:2,59:65] hl[59,65] *}

## Check the Docs UI

We can then go to the docs UI and see the new *path operation*.

<img class="shadow" alt="Interactive API docs UI" src="/img/tutorial/fastapi/read-one/image01.png">

## Recap

You can combine **FastAPI** features like automatic path parameter validation to get models by ID.
