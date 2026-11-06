# fractera-redis-cache — the fast store of a Fractera node

A native element of the node, built on the Fractera native element template (v0.1.20). It is the fifth element of the node's
memory, next to **data** (the database), **storage** (files), **vectors** and **graph**.

**What it is for.** Applications have busy actions: likes, views, reactions, comments waiting to be written. Writing each one to the
database on every click loads the main application. The fast store is meant to take these counters and queues into Redis, in
memory, and to pass the totals to the database element in batches. The truth stays in the database element, so the fast store
keeps no backup of its own.

## Today: a body

Step 560 (owner 2026-10-22: «final dev will in server later, now only base and body with turn off state») built only the body:

- the element folder, its passport and node contract, a record in the core registry (`WEB4-ITEMS-REGISTRY/web4-items.json`);
- since step 619 the passport no longer says `power.default off` (the owner 2026-10-30: «все нативные элементы должны быть
  установлены … По умолчанию отключены остаются только: – страйп Все остальные по умолчанию активны»): the node starts it like every
  native element; `power.reason` stays for when it is turned off (`npm run element:power -- cache status` in the core prints it);
- the core shows it in the left menu, group **Memory**, with the reason on its pages.

**What it does not do yet:** there is no Redis, no door, no transfer of totals, no schedule. Running, it serves its landing (node step 660: what it is for and
where it stands) and nothing else.

## Where it runs

macOS and Linux (owner 2026-10-22: «mac and linux»). Redis is not built for Windows; on Windows the element stays off.

## When it is built further

The next step (on a server, by the owner's word) chooses the engine (Redis or a protocol-compatible one), its doors (through the
database element, `/service/cache/*`, or direct) and how totals reach the database. Any timer or background transfer is a behaviour
of the system and is built only by the owner's word, with its cost in memory named first.

## In the Fractera project

The code is open under the MIT license and the copy on your node is yours. The node installs this element from this repository
(`Fractera/fractera-redis-cache-starter`) by the tag written in the core registry; the core does not let you delete a built-in element
or move its address.
