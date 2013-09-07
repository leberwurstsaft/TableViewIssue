TableViewIssue
==============

Weird UITableView issue that blocks cell selection

Stackoverflow question about the problem: http://stackoverflow.com/questions/18676658/set-uitableviewcell-selected-to-yes-in-willdisplaycell-and-the-cell-cant-be-de

Update (Solution)
===
Never set the selection state yourself. Just use ```selectRowAtIndexPath:animated:scrollPosition:``` for all the rows you want to pre-select,
somewhere after you reload the table view data, or for example in ```-viewDidLoad```.

The question
---

I want to pre-select some rows in a multiple selection UITableView.

I do this in ```tableView:willDisplayCell:forRowAtIndexPath:``` by simply setting ```[cell setSelected:YES animated:NO];```.

However, for some reason this disables deselection for these rows. The embedded controls still work, and so do detail disclosure buttons.

I have uploaded a sample project here: https://github.com/leberwurstsaft/TableViewIssue where you can check out the behavior (in ```Viewcontroller.m``` lines 49-51).

```objective-c
- (void)tableView:(UITableView *)tableView willDisplayCell:(UITableViewCell *)cell forRowAtIndexPath:(NSIndexPath *)indexPath {
    [cell setSelected:NO animated:NO]; //   -->   setSelected:YES and the cells can't be deselected anymore...
}
```

What seems to be the problem?
