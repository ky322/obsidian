### Devices to Store Data On 
From higher capacity and faster access
- Tape Storage
	- Bits as magnetic information on tape
	- Slow access (10s of seconds)
	- Moderate read speed (300MB/second)
	- Very cheap ($0.02 per Gigabyte)
	- Used for long term archival
- Hard Disk
	- Bits as magnetic information on platter
	- Patters spin under read/write heads
	- Slow access (10s of milliseconds access times)
	- Moderate read speed (200MB/second)
	- Cheap ($0.035 per Gigabyte)
- Solid State Drives
	- Bits as small electric charges
	- Elevated price ($0.25 per Gigabyte)
	- Limited number of write cycles (memory wear)
- Main memory
	- Bits as small electric charges
	- Expensive (dollars per Gigabyte)
	- Very fast access (order of nanoseconds)
	- High bandwidth (Gigabytes per second)
	- Used to access hot data - all if economically feasible
- Caches
	- Bits as small electric charges
	- Organized as cache hierarchy
	- Very expensive (hundreds of dollars per Gigabyte)
	- Near instantaneous access (few nanoseconds)
	- Very high bandwidth (tens of Gigabyte per second)

### Relevance for DBMS
- Capacity limits force data to lower parts of the hierarchy
- Data access speeds become bottleneck
	- Design algorithms to minimize data movements
- Random data access is expensive
	- Read data in larger chunks
	- Keep relayed data close together
- Take into account volatility for recovery consideration



### Tables as Files
- Table schema information is stored in database catalog
- Table content is stored as collection of pages (file)
- Each page stores a few KB of data
- Enough to store multiple rows but not entire table

### From Files to Pages
- Store pages as doubly linked list
	- Each page contains pointers to next/prior page
	- Can use separate lists for full/partially empty pages
	- Reference to header page stored in DB catalog
- Directory with pointers to pages
	- Directory pages references data pages with meta data

### From Pages to Slots
- Pages are divided into slots
- Each slot stores one record (table, row)
- Can refer to records via pageID, slotID
- Multiple ways to divide pages into slots
- Fixed length vs variable length records

### Fixed Length Records
- Number of bytes per slot is determined a-priori
- Need to keep track of which slots are used (insertions)
- Packed representation uses consecutive slots
	- Only keep track of number of slots used
- Unpacked representation allows unused slots in between
	- Need bitmap to keep track of used slots
### Variable Length Records
- Records with variable-length text fields
- Number of byte per slot is not fixed a -priori
- Each page maintains directory about used slots
	- Store first byte and length of slots
- Flexibility to move around records on page
	- Can use that for regular compaction

### From Slots to Fields
- Divide each slot into fields
- Fixed length vs variable length fields
- Fixed length: Store field sizes in database catalog
- Variable length: Store field sizes on page
	- Use special delimiter symbol between fields
	- Store field directory at beginning of record