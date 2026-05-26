---
layout: ../../layouts/ArticleLayout.astro
title: "Stalwart: Four Machines One Network"
date: 2026-05-16
pinned: true
hidden: false
author: Collin DeSantis
tags: ["home server"]
description: "My home-made home-server that allows for everything everywhere all at once"
lede: "My home-made home-server that allows for everything everywhere all at once"
image: /images/history_of_information.png
imageCaption: "`❀ Image: Ken Thompson (seated) and Dennis Ritchie at a PDP-11, Bell Labs, c. 1972. Photo: Peter Hamer / Bell Labs`"
---

Earlier this year I began contributing to <a href="/articles/open-source-ecology/" class="lc-header-btn" style="color:#1d4ed8">[Open Source Ecology]</a>. In February I spent a week at OSE's campus building out the hangar. In March I spent two weeks at my father's house in Florida building out Iconic CAD. The kicker is: I live in New Jersey. So how does a desktop guy manage on a small-screen laptop thousands of miles from home? The answer: stalwart server.

Stalwart is the name of my custom made home server running in my garage. I pieced it together with hardware from old gaming computers. I started building out stalwart server and my network because I needed to be in all those different places at once. Stalwart is the key because it meshes four devices together.

<figure class="article-hero">
  <img src="/images/stalwart-garage.jpg" alt="Stalwart in the garage" loading="lazy" />
  <figcaption><code>❀ Image: Stalwart (located to the left of desk and under the desktop PC in identical case) in it's natural habitat: my garage with way too many things going on</code></figcaption>
</figure>

My laptop, my desktop, and the raspberry pi that hosts this site all orbit around Stalwart. If I can reach Stalwart from my laptop then I have access to the whole network. When I arrive at OSE's campus my desktop's files are sitting right there for use on my laptop. When I'm sitting in the OSE workshop on my laptop I can write to the pi or modify any service on Stalwart. When I return to New Jersey all of my Iconic CAD work is sitting right there on my desktop. This whole system lives off of two tools: WireGuard & Syncthing.

You can think of <a href="https://syncthing.net" class="lc-header-btn" style="color:#1d4ed8" target="_blank" rel="noopener noreferrer">[Syncthing]</a> as a folder that exists on multiple devices at once. It's so simple even a grandma could get it. The two devices meet each other and shake each other's hands. They pass a folder from one to another, back and forth, forever. In my case it sits on the desktop and laptop sharing all of my working files using the server as a middleman. I even routed my phone's camera folder straight to the network. No more emailing myself pictures.

<a href="https://wireguard.com" class="lc-header-btn" style="color:#1d4ed8" target="_blank" rel="noopener noreferrer">[Wireguard]</a> does the dirty work that syncthing cannot. It is NOT simple enough for a grandma to understand but she may understand it as 'a magical wire across the sky'. This particular wire connects my laptop to Stalwart. I can type `ssh server` into my terminal and voila full access to Stalwart and the Pi. I can maintain, upgrade, and edit Stalwart + deploy new articles to this site from across the world with this magical wire.

Naturally with home servers the sky is the limit. I already run a <a href="https://getmonero.org" class="lc-header-btn" style="color:#1d4ed8" target="_blank" rel="noopener noreferrer">[monero node]</a> & <a href="https://geti2p.net" class="lc-header-btn" style="color:#1d4ed8" target="_blank" rel="noopener noreferrer">[i2p router]</a> on Stalwart. Though, again, the laptop can access this from anywhere in the world, this is considered a dormant home server. You can think of this as the foundation, the wheels, the first steps to much more. V2 is coming with self-hosted AI, a git instance, systemd-less, and the rest of the fixings. Stalwart has to walk before it can run.