---
coding: utf-8

title: Ecosystem Effects of Web Packaging
docname: draft-yasskin-wpack-ecosystem-effects-latest
category: std

ipr: trust200902

stand_alone: yes
pi: [comments, sortrefs, strict, symrefs, toc]

author:
 -
    name: Jeffrey Yasskin
    organization: Google
    email: jyasskin@chromium.org

--- abstract

This document analyzes how Web Packaging may affect the web ecosystem.

--- note_Note_to_Readers

Discussion of this draft takes place on the wpack mailing list (wpack@ietf.org),
which is archived at <https://www.ietf.org/mailman/listinfo/wpack>.

The source code and issues list for this draft can be found
in <https://github.com/jyasskin/wpack-ecosystem-effects>.

--- middle

# Introduction

Web Packaging, as currently defined in {{?I-D.yasskin-wpack-bundled-exchanges}}
and {{?I-D.yasskin-http-origin-signed-responses}}, is a system to allow content
authored by one web origin to be retrieved in an optionally-trustworthy way from
a peer or other intermediate server. The [ESCAPE
conference](https://www.iab.org/activities/workshops/escape-workshop/) was
chartered to (among other things) look for any increase in consolidation that
might result from standardizing Web Packaging. The known possible effects on
centralization and power imbalances, arranged by the type of service provider,
and not filtered by benefit, harm, or likelihood, follow.

# General

* The implementation of any new technology is a smaller fraction of a large
  organization's budget, which pushes toward centralization.

# Aggregators

* Aggregators' primary power comes from ranking: telling people that they
  probably want to visit particular URLs. That's not affected by packaging.

* Aggregators already rank based on sites' content and technology choices. e.g.
  Google's promotion of HTTPS sites. Packaging can give the aggregator more
  certainty about the user's experience, which might lead to more intrusive
  requirements.

  For example, the Google Search Carousel might be able to insist on particular
  Javascript that could handle swipe gestures where they might not be willing to
  rely on just having seen such JS on the last crawl. However, packaged
  Javascript must also be able to reload the page from the origin to deal with
  retracted content, and that could break reliance on knowing the exact content
  in the same way.

* Prefetch improves navigation speeds from aggregators that can predict which
  links users will click. The ability to make that prediction is an economy of
  scale which encourages centralization. This is likely to have more effect for
  some kinds of aggregators (search engines?) than others (news streams?).

# Browsers

* Packages add pressure to have just one or a few versions of a site's content,
  which might reduce publishers' willingness to support lots of different
  browser engines with different features. They'll either settle on the lowest
  common denominator with some progressive enhancement or target the most
  popular couple engines, which is likely to be Chromium (Google Chrome, Edge,
  Brave, Samsung Internet, Opera, UC Browser, etc.) and WebKit (Safari),
  disadvantaging Gecko (Firefox).

  However, "we only tested in Chrome" is enough of a problem on the online web
  that it's not clear how big an additional impact packaging can have.

# CDNs

* Adding a new kind of distribution might transfer traffic from CDNs to large
  aggregators, which would reduce CDNs' revenue.

* However, CDNs will still be needed to serve URLs that users type in, bookmark,
  or navigate to via same-site links, so there's disagreement, even among
  employees of CDNs, about the likely size of this effect.

* CDNs might be able to acquire even more traffic by offering package caches to
  let smaller sites take advantage of prefetching.

# Content Producers

* If Web Packages become an additional format publishers need to produce
  (https://xkcd.com/927/), that will advantage the larger publishers who can
  afford the engineering to maintain lots of formats. If instead they replace at
  least 2 of the existing formats (e.g. AMP, Apple News, Facebook Instant
  Articles), that'll reduce that advantage of larger publishers and contribute
  to decentralization.

* If aggregators use packaging to serve a significant fraction of content
  producers' bytes for free, this reduces the amount the producers need to pay
  CDNs, which would allow more marginal content producers to stay profitable,
  increasing diversity.

# Other effects not necessarily related to centralization

* When an aggregator prefetches a web package, the static content will load
  instantly, but ads and other dynamic content will have a visible delay.
  Personalization might have a delay or might be loaded from local storage
  effectively instantly. It's not clear what ecosystem effects the changes in
  loading speed are likely to have.

--- back

# Change Log

RFC EDITOR PLEASE DELETE THIS SECTION.

# Acknowledgements

Thanks to the ESCAPE workshop attendees for coming up with many of the effects
in this document.
