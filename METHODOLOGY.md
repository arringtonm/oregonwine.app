# How it's made

This page explains where the site's facts come from, how each one is checked, and the rules the data follows. It describes the method, not the software behind it.

- [The shape of the data](#the-shape-of-the-data)
- [Where the facts come from](#where-the-facts-come-from)
- [How each record is checked](#how-each-record-is-checked)
- [Records from interviews](#records-from-interviews)
- [Places on the map](#places-on-the-map)
- [Rules we follow](#rules-we-follow)
- [Corrections](#corrections)
- [Known limits](#known-limits)
- [Sources and credits](#sources-and-credits)

## The shape of the data

The site is a graph. Each **record** is either a person or place, or a connection between two of them.

- **People and places** come in six kinds: people, wineries, vineyards, AVAs (American Viticultural Areas), organizations and events. Each has a name, any other names it has gone by, a short summary in our own words, and the years that matter: founded, planted, born.
- **Connections** say how two of them relate, in words a reader would use: founded, owns, made the wine at, buys grapes from, trained under, is located in, is married to. A connection can carry a role ("co-owner", "assistant winemaker") and the years it held.
- **Every record cites its sources.** Each connection carries its own citations, so "David Lett founded The Eyrie Vineyards in 1966" points to the pages that say so, not just to pages about David Lett.

A winery or vineyard that changed its name keeps one record, with its former names and the years each was used, so its history isn't split in two.

## Where the facts come from

Records are built from published sources:

- oral history interviews and their transcripts;
- wineries' and vineyards' own histories;
- newspapers, magazines, books and wine writers;
- retailers' producer notes;
- public records such as federal label approvals and winery permits.

The [list of sources](#sources-and-credits) below names the main ones.

New sources are found by reading widely: archives, back issues and wineries' sites. A language model helps pick out which pages are worth reading for records, and helps draft records from the ones that are. A drafted record is never published as it stands. It has to cite a source, and it goes through the check below like everything else.

## How each record is checked

A record is either **verified** or an **unverified draft**. Drafts are shown, because a cited but unchecked fact is still useful. The site's "Verified records only" filter hides them.

A record becomes verified in one of three ways.

### 1. Reviewed by a person

Someone has read the cited sources and confirmed the record.

### 2. Checked against its sources automatically

A decision model reads the text of each cited page and judges whether it supports the record:

- **What it checks:** the relationship itself, each year and the role. For a person or place, it checks each sentence of the summary.
- **What it takes to pass:** a source must support the central claim, and every detail must be supported, each with a confidence of at least 0.9.
- **Facts spread across sources:** a detail may rest on several of the record's sources read together. A record is never shown as verified on that combined reading alone.
- **The right relationship:** for a connection, the source must state this relationship, not only a different one between the same two. A page saying someone founded a winery doesn't pass for their working there.

**How often it's wrong.** We deliberately corrupted one fact in each of 400 records that had passed and checked them again. The corruptions were:
- a year changed;
- a sentence, a party or a relationship swapped for one that is false.

At the 0.9 threshold, 1.0% still passed.

**Pages the model can't read directly.** Some pages are behind bot protection. These are read from the Internet Archive's copy where there is one. A page that can't be read either way never counts for or against a record.

**Label approvals.** A federal label approval usually names its vineyard only in the artwork, so the model also looks at the label images. In a test of deliberately wrong label claims, including another vineyard the same winery buys from, none passed. The sample was small, so a record supported only by label images says so on the site.

### 3. Confirmed by AVA boundaries

A vineyard's AVA can be confirmed by testing its location against the official AVA boundary maps.

### Every morning

Records a reader has flagged are checked again against their sources and any source the reader suggested.

## Records from interviews

Since October 2026, records also come from the interviews themselves, not only their summaries. The interviews include:
- the Oregon Wine History Archive's oral histories;
- Linfield University's archive videos;
- the Weinnotes podcast.

Each interview goes through these steps:

1. **Transcribed.** The audio is transcribed by speech recognition. The archive's own transcripts are used where it has them.
2. **Drafted.** A language model reads each transcript and drafts the people, places and connections it describes, each with the passage it rests on. A draft whose passage isn't in the transcript word for word is thrown away. Out-of-state employers, and colleges someone merely studied at, are left out unless they connect several people in Oregon wine.
3. **Checked.** The automated check reads each draft against its passage and the record's other sources. Names that look alike, across interviews and against the graph, are paired up for a person to decide whether they are the same.
4. **Reviewed by a person.** Every record is accepted, corrected or rejected by hand before it is added. Corrected spellings replace the misheard ones.

Speech recognition is weakest on names, so these records are the most likely to hold a misspelling or a duplicate. Please report any you find.

## Places on the map

### Wineries

A winery is placed at the address it gives visitors, found in published listings and on its own site.

A winery with no tasting room is placed at the premises on its federal winery permit instead, shown as "Made at", not "Visit". Several labels are often made at one custom-crush address.

### Vineyards

A vineyard is placed in one of three ways, best first:

1. **At its own site,** where a source gives the vineyard's street address or location and says the vines are there.
2. **Roughly,** from how a source describes it: "just west of Winderlea", "on the lower slopes of the Cristom estate". The site says so, and shows the description it rests on.
3. **Inside its AVA,** faintly, when nothing narrower is known.

Every placement must fall inside the vineyard's own AVA, allowing a short distance for roads and survey lines. If it doesn't, it is held back for a person.

### Vineyard outlines

Outlines of the land under vine come from OpenStreetMap. An outline is matched to a vineyard by name or by place, and a person settles the doubtful matches. Where OpenStreetMap has no outline, one can be traced by hand over public-domain aerial photography from the US Geological Survey.

### AVAs

AVA boundaries and the dates each was recognised come from the UC Davis Library's public-domain AVA maps.

## Rules we follow

- **Nothing is guessed.** If no source gives a year, the record has no year. Hedged statements ("I think", "reportedly") don't become records.
- **Where sources disagree, the record says so.** The Eyrie Vineyards' founding is dated 1965 by some sources and 1966 by others, so its record reads "1965 or 1966", with a note. We show every year a source gives rather than choosing one.
- **Corrections are logged.** A correction is made only if the check then supports the corrected record. Each one is logged with the old value, the new value and its source.
- **Addresses are for visitors.** A winery's address is where you can taste, which is often some distance from its vines. It is never used as evidence of where grapes are grown.
- **Private sources contribute facts, not text.** Some records come from a subscriber newsletter. Only the facts are kept, never its wording.
- **A label approval is evidence of a plan, not a sale.** Some approved wines are never released. A connection resting only on approvals says so.
- **Summaries are our own words.**

## Corrections

Corrections come in through [issues](../../issues/new/choose) here, or through **Flag** on any record on the site. A correction with a published source is checked against that source the same way as any other record. If the check supports it, it's made and logged. Everything else goes to a person.

## Known limits

- **Coverage is uneven.** It's strongest for the northern Willamette Valley, where most published history concentrates. Southern Oregon, the Columbia Gorge and Walla Walla are thinner.
- **Expect some misspellings and duplicates,** especially among records from interview transcripts.
- **Not every interview has been read in full yet,** so some careers are less detailed than they could be.
- **Many vineyards have no place on the map yet,** or only a rough one.

## Sources and credits

These are the main sources, by how many records cite them:

- [Oregon Wine History Archive](https://oregonwinehistoryarchive.org), Linfield University: oral history interviews, their summaries and transcripts.
- Weinnotes, a monthly Oregon wine newsletter, and its podcast.
- [Vinopolis Wine Shop](https://www.vinopoliswineshop.com)'s newsletters: producers' stories and the vineyards named on their wines. Critics' reviews they quote are never used.
- [Wine Camp](https://craigcamp.com), Craig Camp's journal.
- [The Prince of Pinot](https://www.princeofpinot.com).
- [Wikipedia](https://en.wikipedia.org).
- [Oregon Wine Press](https://www.oregonwinepress.com).
- [Wine Spectator](https://www.winespectator.com) and [Great Northwest Wine](https://www.greatnorthwestwine.com).
- Wineries' and vineyards' own websites.
- [TTB Public COLA Registry](https://ttbonline.gov/colasonline/publicSearchColasBasic.do) (public domain): federal label approvals.
- TTB's list of wine permittees (public domain): where wine is made.
- [WineEnthusiast reviews, June 2017](https://www.openml.org/d/42074) (OpenML dataset 42074, CC BY-NC-SA 4.0). Only each Oregon review's winery, wine name, region and variety are used, never the reviewers' writing, scores or prices.
- [UC Davis Library AVA boundaries](https://github.com/UCDavisLibrary/ava) (public domain).
- [OpenStreetMap](https://www.openstreetmap.org/copyright) vineyard outlines (© OpenStreetMap contributors, ODbL), kept separate from the site's own data.
- [US Geological Survey](https://www.usgs.gov) aerial imagery (public domain).

Automated source checks use [Jev](https://typesafe.ai) from TypeSafe AI. Drafting uses Claude from Anthropic.
