## Where each requirement is implemented

| Requirement | Where |
|---|---|
| Regular and Honors students | `RegularStudent` and `HonorsStudent` extend the abstract `Student`; `Student.of(type, ...)` creates the right one |
| HashMap O(1) lookup | `StudentManager.students` (`ConcurrentHashMap`, thread-safe hash map) |
| TreeMap GPA rankings | `StudentManager.rankings()` |
| HashSet unique courses | `StudentManager.courses` (concurrent hash set) |
| LinkedList grade history | `Student.history` |
| PriorityQueue of tasks | `BackgroundServices.tasks` |
| Regex validation | `RegexValidator` (used by the menu, CSV, JSON and binary import); every student ID typed in the menu is checked before it is looked up |
| Regex pattern search | `StudentManager.searchByRegex()` |
| NIO.2: Path, Files.lines, BufferedWriter | `GradeFileService` |
| CSV, JSON and binary import | `importCsv()`, `importJson()`, `importBinaryInto()`, all from Files → Import (chosen by file extension) |
| Core and Elective subjects | `CoreSubject` and `ElectiveSubject` extend `Subject`; `SubjectCatalog` lists them. Record grade (option 3) shows them as numbered lists; imports only accept catalog course codes |
| Saving between runs | `DataStore` (load at startup, auto-save on every change) |
| Object serialization | `GradeFileService.exportBinary()` / `importBinary()` |
| WatchService | `FolderWatcher` |
| FixedThreadPool (reports), 2-8 threads | `BackgroundServices.reportPool`, sized by `Main.reportThreads()` (one per CPU core, kept between 2 and 8) |
| CachedThreadPool (stats) | `BackgroundServices.statsPool` |
| ScheduledThreadPool | dashboard every 5 s, daily GPA recalculation at 03:30 |
| SingleThreadExecutor (logging) | `AuditLogger` |
| ConcurrentHashMap + LRU cache | `ReportCache` |
| Streams: map, filter, reduce, collect | `StudentManager.statistics()`, `Student.getAverage()` |
