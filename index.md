# Pekka Nikander

Pekka Nikander is a software architect and lead programmer with over
30 years of industry experience, with an inkling for embedded and things.

I prefer e-mail for communication, and don't answer to cold phone calls.

Email: firstname dot lastname at iki dot fi

Please note that many links below are broken, due to my previous web
site provider trashing my site and not having time to fish the content
back.  If you are interested in any of my papers or past projects,
feel free to send e-mail to me, and I'll add the material to the
website and mail back to you.  I usually respond to e-mail within a
day or two.

## A failed attempt to create a blog

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

## Selected publications

* Pekka Nikander, Andrei Gurtov, and Thomas R. Henderson, ["Host
  Identity Protocol (HIP): Connectivity, Mobility, Multi-Homing,
  Security, and Privacy over IPv4 and IPv6
  Networks,"](publications/hip_survey.pdf) in IEEE Communications
  Surveys and Tutorials, Volume 12 Issue 2, pp. 186-204, April 2010.
* Petri Jokela, Andras Zahemszky, Christian Esteve Rothernberg, Somaya
  Arianfar, and Pekka Nikander, ["LIPSIN: Line Speed Publish/Subscribe
  Inter-Networking,"](http://ccr.sigcomm.org/online/files/p195.pdf)
  SIGCOMM 2009, Barcelona, August 17-21, 2009.
* Tuomas Aura, Pekka Nikander, and Gonzalo Camarillo, ["Effects of
  Mobility and Multihoming on Transport-Layer
  Security,"](publications/aura-nikander-camarillo-ssp04.pdf) in
  Proceedings of IEEE Symposium on Security and Privacy,
  Berkeley/Oakland, California, May 9-12, 2004, IEEE Computer Society.
* Pekka Nikander, Jukka Ylitalo, and Jorma Wall, ["Integrating
  Security, Mobility, and Multi-Homing in a HIP
  Way,"](publications/NDSS03-Nikander-et-al.pdf) in Proceedings of
  Network and Distributed Systems Security Symposium (NDSS'03),
  February 6-7, 2003, San Diego, CA, pp. 87-99, Internet Society,
  February, 2003.
* Jari Arkko and Pekka Nikander, ["How to Authenticate Unknown
  Principals without Trusted Parties,"](publications/cam2002b.pdf) in
  Proceedings of Security Protocols Workshop 2002, Cambridge, UK,
  April 16-19, 2002.
* Pekka Nikander, Kristiina Karvonen, ["Users and Trust in
  Cyberspace",](publications/cam2000.pdf) a position paper, in the
  Proceedings of Cambridge Security Protocols Workshop 2000, April
  3-5, 2000, Cambridge University.

[Full publication list](publications.html)

[Some presentations](presentations)

## Past projects

* [PURSUIT](http://www.fp7-pursuit.eu/PursuitWeb/) (2010-2011)
* [Publish-Subscribe Internet Routing Paradigm](http://www.psirp.org/)
  (2008-2010)
* [Host Identity Protocol](HIP.html) (2000-2006)
* [Bound End-to-end Tunnel](BEET.html) (2003)
* [SEcuring Neighbor Discovery](SEND)
  (2002-2004)
* [IEEE 802.1x for FreeBSD](eapol.html) (2001-2003)
* [Mobile and Multihomed Hosts](homeless) (2001)
* iPoints (2001)
* [FrameMaker templates]() (1992-2001 or so)
* [Java for lego RCX](rcx) (2000)
* [Java Conduits Beans Framework](jacob) (1999-2000)
* [TeSSA](http://www.tml.hut.fi/Research/TeSSA/) (1998-2001)
* [Gang-of-Four Design patterns as UML
  models](GoF-models/html/) (1998)
* Using formal methods to reason about cryptographic protocols (1994-1997)

## Misc historical

* [On Future Internet Architectures: Rethinking Naming, Trust, and Primitives](FIND-white-paper.pdf)
* [Personal contributions to the IAB thinking](IAB/)
* [Generic Proxying as a Deployment Tool](draft-nikander-arch-generic-proxying-00.txt)
* [Why Complexity is like Body Fat](FAT/index.html)
* [IETF-63 ALIEN BoF minutes](ietf63_alien_minutes.html)
* [NDSS 2003: Conference report](ndss2003-report.html)
* [Usenix 2002 ATC report](usenix2002-report.html)



