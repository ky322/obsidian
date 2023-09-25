### Quickly Finding Data
- Table `Enrollment(sid, cid)` links students to courses
	- Search entries for specific students
- Data stored as unordered file - must scan all pages
- Better: data sorted by student ID ; apply binary search
- Problem: Sometimes search for specific courses
- Only one sort order, cannot duplicate data
### Indexes
- Index: Auxiliary data structure for finding data faster
- Exactly same principle as for books
- Can have multiple indexes for same table
	- One index for finding info on specific students
#### How It Works
- Index stores references to data records
	- Store page IDs and slot IDs
- Index group records by values in specific columns
- Columns are the index search key
- Index retrieves records for specific search key values
- Binary search narrows down "search space" by factor 2
- Can we get a higher pruning factor per page read
-  Idea: Non binary search trees

### Index Node Content
-  Content of inner nodes:
- 