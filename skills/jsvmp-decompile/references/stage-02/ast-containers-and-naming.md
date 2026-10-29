# AST containers and naming

Find the original function and the exact container carrying produced nodes. Trace how parameters, temporaries, identifiers, properties, and generated names are allocated. Preserve declaration order, source locations when required, comments, and one-time evaluation. Document collisions and scope ownership.

Write before/after node shapes with a fixture and explain why the generated name is legal in the original scope. Do not normalize names merely for readability if identity or lookup depends on them.
