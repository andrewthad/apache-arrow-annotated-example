# Annotated Example of Apache Arrow/Feather File Format

This is an example where I worked through to figure out the meaning
of every byte in a feather file. I used the specs for
Apache Arrow and flatbuffers to help figure this out. I did this
because I was not able to figure out how to produce a feather file
from the spec alone. By working backwards through an example produced
by a tool already known to be compliant with the spec, I was able
to fill in the gaps in my understanding. I am publishing this in
the hopes that it will spare someone else the difficulty that I
went through. If you are trying to use this, you will still need
to read the two relevant specs. It is learning aid, not a substitute
for a specification.

To make this example, I started with the file at `data.csv`. This is
a list of Oscar winners by year with a boolean column ("alive") that
I added. The values in this column do not actually reflect whether or
not a great thespian is deceased. I just needed to figure out how
arrow encoded boolean columns. I loaded the csv into pyarrow,
did some trick to convince it to map "yes" and "no" to true and false,
and then wrote it out to a feather file. This is what the Arrow spec
refers to as the "IPC File Format", not the "IPC Streaming Format".
The columns are not compressed in any way.
