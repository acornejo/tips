# git-primer

To convert directory to git repository:

    git init
    git add .
    git commit -a -m "First import"

To create a tag, use:

    git tag -a $(tag_name)
    # or
    git tag -s $(tag_name)

To push tags:

    git push --tags
