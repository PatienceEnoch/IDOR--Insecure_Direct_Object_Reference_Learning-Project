# IDOR / Broken Access Control Learning Lab

An authorized TryHackMe exercise I used to understand how insecure direct object references appear in HTTP requests and why server-side authorization matters.

> This repository documents a controlled training environment. It is not a guide for accessing systems or data without authorization.

## The vulnerability

An IDOR occurs when an application accepts an object identifier such as a user ID, account ID, or file ID without correctly checking whether the authenticated user is allowed to access that object.

The important failure is not that an identifier is predictable. The failure is **missing or incorrect authorization on the server**.

## What I practiced

Inside the training environment, I:

- authenticated to the lab application
- inspected application requests
- identified a user-controlled object identifier
- changed the identifier within the authorized exercise
- observed that the application returned data belonging to another object
- documented why the behavior represented broken access control

## Defensive lessons

The useful part of this lab was understanding the fix, not just reproducing the flaw.

Applications should:

- authorize every sensitive object request server-side
- verify resource ownership or permission before returning data
- apply role and policy checks consistently
- avoid treating UUIDs or unguessable identifiers as authorization
- log unusual access patterns that may indicate enumeration

## Why this belongs in my networking portfolio

I am primarily focused on network and cloud engineering, but access control affects the infrastructure I help operate.

This lab gave me a better understanding of what application teams mean when they discuss broken access control, and it reinforces the security habit I want to carry into infrastructure work: **identity and authorization must be enforced at the boundary where access is granted.**

## Related work

- [Network Flight Recorder](https://github.com/PatienceEnoch/network-flight-recorder) — security-aware network evidence, least privilege, guarded remediation
- [Main profile](https://github.com/PatienceEnoch)
