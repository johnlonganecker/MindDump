# Git Tips

### Merge without creating a merge commit
git pull origin --rebase

### Move files to another repo, preserve history
http://gbayer.com/development/moving-files-from-one-git-repository-to-another-preserving-history/

```
git clone <git repository A url>
cd <git repository A directory>
git remote rm origin # make sure we don't push anything back to origin
git filter-branch --subdirectory-filter <directory 1> -- --all
```
**More details in above link**
