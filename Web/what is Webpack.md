By Ciel

Webpack is a module builder. This is important to understand, as Webpack does not run during your page, it runs during your development.

Webpack is a tool wherein you use a configuration to explain to the builder how to load specific things. You describe to Webpack how to load *.js files, or how it should look at .scss files, etc. Then, when you run it, it goes into your entry point and walks up and down your program and figures out exactly what it needs, in what order it needs it, and what each piece depends on. It will then create bundles — as few as possible, as optimized as possible, that you include as the scripts in your application.

A module loader is usually a tool or a script through which a developer passes their JavaScript through — this tool (or script!) is responsible for determining load priority, dependencies, efficiency, paths, etc. It is a worker whose job is to make your scripts run like you expect without worrying about the overhead.

[source](https://medium.com/the-self-taught-programmer/what-is-webpack-and-why-should-i-care-part-1-introduction-ca4da7d0d8dc)