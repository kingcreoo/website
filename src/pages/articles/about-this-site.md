---
layout: ../../layouts/ArticleLayout.astro
title: About This Site
date: 2025-11-21
description: Its purpose, how it was made, and why it exists.
tags: [meta]
image: /images/rune-1.png
---

This is a personal site hosted on a Raspberry Pi Zero 2W, built with Astro, and served as static HTML through nginx. There is no database, no client-side framework, and no JavaScript required to read anything published here.

## Why It Exists

Most of the internet is built to extract attention. This site is built to hold thoughts. Logs record what happened. Articles work through what it means. The two reference each other over time.

## How It Works

Every page is a flat HTML file generated at build time. The source lives in a git repository. When something is ready to publish, the site rebuilds and rsyncs the output to the Pi. The whole process takes a few seconds.

## What It Runs On

A Raspberry Pi Zero 2W drawing about 0.4 watts at idle. The machine sits on a shelf next to the router. It serves static files and nothing else. If the power goes out or the SD card dies, the site rebuilds from the repo in minutes.

## The Stack

- **Astro** for static site generation
- **nginx** for serving files
- **System fonts** only — no external requests
- **No analytics, no cookies, no tracking**

The goal is a site that loads instantly, costs nothing to run, and survives without maintenance.
