# Canvas Helpers
A collection of Python scripts to help make common [Canvas](https://www.instructure.com/canvas) tasks more manageable.

Begin by adding your Canvas API key in [canvashelpers.config](https://github.com/simonrob/canvas-helpers/blob/main/canvashelpers.config), then read the guides below to get started.
Each script also has a `--help` option that provides further detail.

## Scripts and functions
- [Attachment file/comment/mark uploader](feedbackuploader.py): When assignment marks are processed outside of Canvas, they can already be uploaded in bulk from a spreadsheet using the existing tools (import/export grades).
But it is not possible to add comments or upload attachments in this way (except through an [awkward hack](https://ltech.ljmu.ac.uk/wp-content/uploads/2017/04/Batch-Uploading-Student-Submissions-and-Feedback.pdf)), which means a tiresomely repetitive task of attaching these documents one-by-one.
This script allows you to upload a set of feedback attachments, grades and/or generic or individual text comments in bulk, and is compatible with both individual assignments and group-based ones.
Usage: Place your attachment files in the script's working directory, named according to students' Canvas Login IDs (typically their institutional student numbers) or their group names, then run `python3 feedbackuploader.py [assignment URL]`.
See `python3 feedbackuploader.py --help` for further options.

- [Student identifier](studentidentifier.py): Canvas sometimes seems to try quite hard to hide the fact that students typically have an institutional identifier
(i.e., student number) that is different to their Canvas ID.
This script adds a new custom column in a course's Gradebook that shows student numbers
Note: by default, courses often have a hidden custom column called 'Notes' that
is private to the course teacher.
Only one private column is allowed per course, so this column will be replaced *and any existing data lost* if it is present.
Usage: `python3 studentidentifier.py [course URL]`
See `python3 studentidentifier.py --help` for further options.

- [Submission downloader/renamer](submissiondownloader.py): Canvas allows you to bulk download students' submission files, but does not give any control over their naming.
It can be useful to have these files named according to students' numbers or group names, which is what this script does.
Downloaded submissions are saved in a folder named as the assignment ID.
Usage: `python3 submissiondownloader.py [assignment URL]`.
See `python3 submissiondownloader.py --help` for further options.

- [WebPA manager](webpamanager.py): [WebPA](https://webpaproject.lboro.ac.uk/) is a useful way of incorporating team member contribution feedback when running group-based assignments.
This script helps run an offline version of this process using spreadsheets uploaded to a Canvas assignment, and handles both form generation and mark scaling.
See `python3 webpamanager.py --help` for further instructions.

- [Quiz result exporter](quizexporter.py): When using quizzes as assignments that need review or processing of some form (rather than just predetermined correct/incorrect responses), the "New Quizzes" feature on Canvas is far worse than the old version, and—most importantly, for large class sizes—does not allow bulk response export.
After significant community resistance, Canvas developers Instructure have now [relented](https://community.canvaslms.com/t5/Quizzes-Transition/Transparency-into-Quizzes-Planning/ta-p/502615) and may at some point implement this missing feature.
In the meantime, this script allows you to export all quiz responses to an XLSX spreadsheet.
Usage: `python3 quizexporter.py [assignment URL]`

## Additional resources
- [Python module for working with the Canvas API](https://canvasapi.readthedocs.io/en/stable/index.html)
- [Canvas API reference](https://canvas.instructure.com/doc/api/index.html)
- [Canvancement](https://github.com/jamesjonesmath/canvancement): JavaScript extensions for Canvas
- [Pages Data Merge](https://iworkautomation.com/pages/script-tags-data-merge.html): Create Pages/PDF documents automatically from a Numbers spreadsheet


## License
[Apache 2.0](LICENSE)
