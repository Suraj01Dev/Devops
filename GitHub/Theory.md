1. What are the 3 stages in Git ?
	- `Modified state `
	   This is a state where the files are modified, but not committed to the DB.
	   
	- `Staged state`
	   In this state the files are marked for getting committed in the next commit
	   
	- `Committed state`
	   In this stage the files are saved in the local git DB.

2. What is a commit and what is a commit object ?
	Committing in GitHub is similar to saving, it saves a record of the edited changes. a commit object contains the following
	- Name of the commit
	- Email of the committer
	- Commit Message
	- Pointer to its parent
		- 0 parents for initial commit
		- 1 parent for normal commit
		- multiple parents for commit that merged from multiple branches.

