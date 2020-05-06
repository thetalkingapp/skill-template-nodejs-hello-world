# ask-isp-json
Template JSON files for Alexa skill in-skill products (aka, ISPs)

The ASK CLI version 1.x would automatically create JSON descriptor files for in-skill products
when the `ask add isp` command ws used. Unfortunately, that feature was removed in ASK CLI v2.0.0
and is unlikely to be reinstated.

Because the ISP JSON files are 50+ lines long, the `ask add isp` command is much more convenient
than creating those files by hand. Even so, the files produced by `ask add isp` are just templates
requiring manual editing to be useful.

I'm placing the template files here as a convenience for lack of an equivalent command in ASK CLI v2.
Copy the relevant file to your project and edit the TODO entries. Then use the ASK CLI to create the
product.
