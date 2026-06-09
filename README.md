# Crawling Daily Survey, Poll & Exchanges News of the Cross-Strait Issues

## Introduction

The repo aims to obtain the daily news of **the latest survey or poll** on the cross-strait issues and **the cross-strait exchanges** among the local governments automatically by means of web scraping.

## Programming Schedule

- The program executes via the scheduler ``Cron``.
- The scheduling time: every **UTC+8** ``4 a.m.`` ``7 a.m.`` ``12 p.m.``
- Crawing the news published ``24 hr`` ago.

## Diagram

The processing workflow shows below:

```mermaid
flowchart TD

A(("Search Engine"))
B["Pew"]
C["Gallup"]
D["Media"]
E@{ shape: procs, label: "other sources"}
F@{ shape: curv-trap, label: "Polls" }
G@{ shape: curv-trap, label: "Exchanges" }
H@{ shape: docs, label: "Receivers"}

subgraph "News Links"
B
C
D
E
end

subgraph "Email"
F
G
end


A--Crawing-->B
A--Crawing-->C
A--Crawing-->D
A--Crawing-->E

B--"Output"-->F
C--"Output"-->F
D--"Output"-->F
D--"Output"-->G
E--"Output"-->F
E--"Output"-->G
F--"Send"-->H
G--"Send"-->H

```
