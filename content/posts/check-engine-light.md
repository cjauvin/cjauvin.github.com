---
title: "Ignore Your Check Engine Light at Your Own Peril"
date: 2025-10-05T12:26:37-04:00
draft: false
---

Currently in my car I have the "check engine" light being on, but it's ok,
because I know what is the problem, my mechanic told me that it's `<something>`,
and that even though it's not ideal, it can wait while he finds the part to
repair it (apparently it's not so easy to find).

![](/images/check-engine-light.jpg)

There is something I don't like about this though: if there is a NEW problem
appearing, I won't know about it, because this check engine light has only one
state, and now it's being used.

On a computer of course the situation is quite different. You have thousands of
sources of notifications, warnings and potential errors, and you need ways to
manage them, in order to avoid drowning in noise. One source of noise I find
particularly annoying and stressful is the notification that you need to update
something. I find it difficult because in many cases, you are torn: on one side
you are attracted by the novelty and the possibility of the newer version of
something being *better*, but on the other, there is always the real possibility
that upgrading a component will introduce a *new* problem (in software
development this is so common and problematic that it has its own name: a
regression). I don't know if it is because I'm OCD or whatever, but I often find
that hard to manage, and with time, I have been moving quite clearly on the
conservative side of things: for instance, there is no way you will find me
eagerly upgrading to the new version of MacOS (Tahoe something I think), even
though I know in advance that the upgrade warnings will annoy me. I will
certainly wait for a couple of `.x` versions to pass. Some colleagues of mine
were very early MacOS upgraders, and I was horrified by it. Why would you take
the chance to render such a complex work tool useless because you are too eager
to try a shiny new UI feature? By the way, I have a similar "subtly stressful"
relationship with unread notifications, but that is another story.

While doing software development, there is a deeper peril related to this, for
which I had two painful experiences recently, while using Claude and Codex to
code. The first one happened when I asked Claude to give me some code for the
build recipe of a Docker container:

```docker
ARG LO_URL="https://downloadarchive.documentfoundation.org/libreoffice/old/6.4.7.2/deb/x86_64/LibreOffice_6.4.7.2_Linux_x86-64_deb.tar.gz"
WORKDIR /tmp/lo
RUN wget -q "$LO_URL" -O lo.tar.gz \
 && tar -xzf lo.tar.gz \
 && cd LibreOffice_6.4.7.2_Linux_x86-64_deb/DEBS \
 && dpkg -i *.deb || true \
 && apt-get update && apt-get -f install -y
```

Can you spot the problem? I will make it easier for you, by showing you a second
instance of the same problem, this time offered by Codex, while helping me code
something in Python:

```python
def api_request(
    method: str, endpoint: str, data: Optional[Dict[Any, Any]] = None
) -> Optional[requests.Response]:
    """Make authenticated API request"""
    try:
        url = f"{API_BASE_URL}{endpoint}"
        headers = get_headers()

        if method.upper() == "GET":
            response = requests.get(url, headers=headers)
        elif method.upper() == "POST":
            response = requests.post(url, json=data, headers=headers)
        elif method.upper() == "PUT":
            response = requests.put(url, json=data, headers=headers)
        elif method.upper() == "DELETE":
            response = requests.delete(url, headers=headers)
        else:
            return None
    except Exception:
        return None
```

Can you see it now? Yes of course, in both cases, the AI decided that it was a
*good thing* (tm) to send any errors in a black hole (the first time with the
`true` command, and the second time with the dreaded `except Exception` Python
pattern), and both times, I lost a lot of time, wandering completely in the
dark, because there was no "stop the world, an error occurred!" safety net. What
is notable in those two cases is that it's quite hard to come with any good
reason for these two draconian error silencing mechanisms, in the first place.
In both cases, if there is an error at this particular stage, it should be an
immediate showstopper, and the underlying problem should be investigated in
priority. Silencing these errors is a very risky strategy, and one thing is
certain: it shouldn't be the default solution that is being offered by an AI
coding agent, whatever the context. Please AI coding agents, you should learn to
NOT do that!