# Dolphin ONE Taxi Apps - Calll integration guide

## Table of Contents
* [Overview](#pverview)
* [Phone call resources](#phone-call-resources)


## Overview
This document provides some guidance, to allow dispatch software developers to build API endpoints which we can interact with when a telephone call is received. We can create a request in virtually any format.  However, to provide easy integration, we have some standards which will allow easy integration.

The responses can also be in virtually any format, as long as we can get the data that we need.

Our preferred integration methods:
* Node.js client library
* REST API

## Phone call resources

| Methods | Description |
| --- | --- |
| [invite](methods/invite.md) | Start a new inbound call. |
| [ringing](methods/ringing.md) | Show a call ringing at an agent phone(s). |
| [missed](methods/missed) | Report a missed call (to allow a call back / update statistics). |
| [connected](methods/connected) | New connected call |
| [cleared](methods/cleared) | A call has ended |
