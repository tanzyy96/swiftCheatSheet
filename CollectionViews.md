# Collection View

### 1. Intro to Collection Views
Collection Views are very similar to table views. There are several steps when it comes to using a Collection View Controller.

1. Declare VC as UICollectionViewController (protocol)
2. Add protocol methods:
  1. numberOfItemsInSection
  2. cellForItemAt
  3. (optional) didSelectItemAt

For Collection Views, instead of using indexPath.row, we want to use indexPath.item instead. IMPORTANT.
