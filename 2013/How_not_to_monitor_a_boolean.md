We were lazy and wrote a simple PostgreSQL monitoring check in shell instead of
using some proper language. The code looked about this:

<pre>
out=$(psql -tAc "SELECT some_stuff, t > now() - '1 day'::interval FROM some_table" some_db 2>&1)
case $out in
	*t) echo "OK: $out" ;;
	*) echo "NOT OK: $out" ;;
esac
</pre>

If the string ends with 't', all is well, if it ends with 'f' or someting else, something is wrong.

Unfortunately, this didn't go that well:

<tt>OK: psql: FATAL:  database "some_db" does not exis<em>t</em></tt>

[[!tag debian postgresql]]
