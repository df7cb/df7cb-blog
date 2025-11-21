---
title: "Salsa batch import"
date: 2018-02-04T09:21:05+01:00
tags:
- debian
---

Now that <a href="https://salsa.debian.org/">Salsa</a> is in
<a href="http://blog.snow-crash.org/blog/salsa.debian.org-git.debian.org-replacement-going-into-beta/">beta</a>,
it's time to import projects (= GitLab speak for "repository"). This is
probably best done automated. Head to
<a href="https://salsa.debian.org/profile/personal_access_tokens">Access Tokens</a>
and generate a token with "api" scope, which you can then use with curl:

<pre>
$ cat salsa-import
#!/bin/sh

set -eux

PROJECT="${1%.git}"
DESCRIPTION="$PROJECT packaging"
ALIOTH_URL="https://anonscm.debian.org/git"
ALIOTH_GROUP="collab-maint"
SALSA_URL="https://salsa.debian.org/api/v4"
SALSA_GROUP="debian" # "debian" has id 2
SALSA_TOKEN="yourcryptictokenhere"

# map group name to namespace id (this is slow on large groups, see https://gitlab.com/gitlab-org/gitlab-ce/issues/42415)
SALSA_NAMESPACE=$(curl -s https://salsa.debian.org/api/v4/groups/$SALSA_GROUP | jq '.id')

# trigger import
curl -f "$SALSA_URL/projects?private_token=$SALSA_TOKEN" \
  --data "path=$PROJECT&namespace_id=$SALSA_NAMESPACE&description=$DESCRIPTION&import_url=$ALIOTH_URL/$ALIOTH_GROUP/$PROJECT&visibility=public"
</pre>

This will create the GitLab project in the chosen namespace, and import the repository from Alioth.

Pro tip: To import a whole Alioth group to GitLab, run this on Alioth:
<pre>
for f in *.git; do sh salsa-import $f; done
</pre>

(*Update 2018-02-04*: Query namespace ID via the API)
