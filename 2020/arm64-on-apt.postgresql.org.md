[[!meta title="arm64 on apt.postgresql.org"]]

The <a href="https://apt.postgresql.org/">apt.postgresql.org</a> repository has been extended
to cover the <em>arm64</em> architecture.

We had occasionally received user request to add "arm" in the past, but it was
never really clear which kind of "arm" made sense to target for PostgreSQL. In
terms of Debian architectures, there's (at least) armel, armhf, and arm64.
Furthermore, Raspberry Pis are very popular (and indeed what most users seemed
to were asking about), but the raspbian "armhf" port is incompatible with the
Debian "armhf" port.

Now that most hardware has moved to 64-bit, it was becoming clear that "arm64"
was the way to go. Amit Khandekar made it happen that
<a href="https://intl.huaweicloud.com/en-us/">HUAWEI Cloud Services</a>
donated a arm64 build host with enough resources to build the arm64 packages
at the same speed as the existing amd64, i386, and ppc64el architectures.
A few days later, all the build jobs were done, including passing all
test-suites. Very few arm-specific issues were encountered which makes me
confident that arm64 is a solid architecture to run PostgreSQL on.

We are targeting Debian buster (stable), bullseye (testing), and sid
(unstable), and Ubuntu bionic (18.04) and focal (20.04). To use the arm64
archive, just add the normal sources.list entry:

<pre>
deb https://apt.postgresql.org/pub/repos/apt buster-pgdg main
</pre>

<h2>Ubuntu focal</h2>

At the same time, I've added the next Ubuntu LTS release to apt.postgresql.org:
focal (20.04). It ships amd64, arm64, and ppc64el binaries.

<pre>
deb https://apt.postgresql.org/pub/repos/apt focal-pgdg main
</pre>

<h2>Old PostgreSQL versions</h2>

Many PostgreSQL extensions are still supporting older server versions that are
EOL. For testing these extension, server packages need to be available. I've
built packages for PostgreSQL 9.2+ on all Debian distributions, and all Ubuntu
LTS distributions. 9.1 will follow shortly.

This means people can move to newer base distributions in their .travis.yml,
.gitlab-ci.yml, and other CI files.

[[!tag debian postgresql]]
