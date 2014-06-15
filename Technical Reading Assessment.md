#Technical Reading Assessment: [Ryan Bigg's Developing a RubyGem using Bundler] [1]#
[1]: https://github.com/radar/guides/blob/master/gem-development.md

1.  **What does the command "bundle gem foodie" do?**

	This command creates a scaffold directory for the gem we will call "foodie" (keeping things organized and easy to find) and (if Git is installed) initializes a Git repository in that directory so we can start committing our code right away.

2.  **In what folder do we put our test files?**

	We create a folder called "spec".  For the example provided in the reading, the name of the file was 
	
	`spec/foodie_spec.rb`

3.  **What do we need to write to add the activesupport (Version 4.0.0) dependency to our gemspec?**

	We need to write a line of code that says:
	
    `spec.add_dependency "activesupport", "4.0.0"`

	This allows our gem to use methods from the "activesupport" gem in the gem we creating.  No need to rewrite the wheel, after all.
	
	Also of note: this line of code allows me to add dependency for activesupport version 4.0.0 and ONLY that version.  If I wanted to allow for some version flexibility in the future, it's suggested I write:
	
    `spec.add_dependency "activesupport" "~> 4.0.0"`

4.  **What steps need to be taken to write a generator?**
	1.  Define the generator class.  This is a subclass of Thor::Group
		- Name the file for this class and require it.  This tells our gem this file is necessary for its operation.
		- Include Thor::Actions . This will allow us to use helper methods for doing things like creating files and directories.
	2. Define the methods in this generator class.
	3. Write the templates this generator will use to generate its files.
	4. Define the source_root that tells the generator where to find the templates we created.
	5. Test it to make sure it works.
