## Variables and User Input

Variables are at the heart of any programming or scripting language, and Bash is no exception.
They allow you to store data (like filenames, dates, paths, and user inputs) that can be reused and modified throughout your script.

### What is a Variable?

A variable is a name for a value that you can store and reference later. It's simply a placeholder.

Let's look at how we define variables:

```bash
#!/bin/bash
name="Najeeb"
role="Data Engineer"

echo "Hello, $name! Your role is $role."
```

What's hapenning here?

The `name` and `role` are our variable, we are then referencing their value  using `$` in the sentence.

- Notice that there are no spaces aroun the `=` sign.
- name = "Najeeb" will cause an error.
- Use `$variable` to access the value.
- Always quote variable references (`"$name"`) to handle spaces safely.
