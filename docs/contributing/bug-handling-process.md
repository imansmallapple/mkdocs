
Eclipse Oniro is aiming to build a secure system from the foundation, applying the
best industry practices in terms of development quality. However, as in
every software projects, bugs do happen. This process explains how we
handle bugs.

## How to Report a Bug?

If you think you have found a bug in our distribution, please file a bug
report in our [bug
tracker](https://github.com/eclipse-oniro4openharmony/manifest/issues) and in the project that you think is the
source of the issue. Use the provided template:

- The module affected
- What is the action to reproduce the bug? (Steps to reproduce)
- What is the result you see? (Actual result)
- What is the result you expect? (Expected behaviour)
- Frequency? (always, sometimes, one-time issue)
- Tested version (image name and version, platform)
- Do you know any workaround of this issue? (link to
  workaround/mitigation steps etc)
- Do you have a fix for this issue?

Developers review the reported issues and perform triage (see below).
When a fix is available, the ticket is updated with the details of the
solution.

## Bug Triage

The bug triage is a process where developers asses the bug and set its
severity and domain. At the end of this process the bug will:

- Be classified as a security issue, normal bug, feature request, or
  be rejected if the feature is working as planned or could not be
  reproduced.
- Have its severity set. Please refer to the documentation of severity
  levels below.
- Have its domain set. The bug tracker will include the latest list.

If the bug is classified as a security vulnerability, the engineer
assesing the issue will create a new ticket in the private security bug
tracker and the discussion will continue in the security bug tracker
from that point. Please refer to the CVE Process for details.

If the bug is confirmed as a bug, the developer will assign bug
severity: critical, normal, minor or low.

**NOTE：**

_Critical_ severity bugs make a feature unusable, cause a major data
loss or hardware breakage. There is no workaround, or a complex one.
_Normal_ severity bugs make a feature hard to use, but there is a
workaround (including another feature to use instead of the desired
one). _Minor_ severity bugs cause a loss of non-critical feature (like
missing or incorrect logging). _Low_ severity bugs cause minor
inconveniences (like a typo in the user interface or in the
documentation).

The bug can originate in a package developed by the project, or from one
we use from an upstream source. The process of handling a bug report
will change between those two cases:

### When the Issue is in the Code Developed by the Project

In the case where the bug originates in the code directly maintained by
the Project, the bug is handled directly in the bug tracker.

### When the Issue Originates from Upstream Code

If the issue was identified in upstream code, we report an upstream
issue in a way appropriate to the upstream project. We store the
reference to the upstream bug report in our bug tracker. Depending on
the bug severity, we might decide to develop and maintain a fix locally.
However, we strongly prefer to upstream the fix first, and then get it
with a regular upstream code update.

Please note also that we periodically update maintained packages from
upstream sources, regardless of the bugs filled in our system. Our goal
is to update to the latest stable version of the package.

## Detailed Workflow

### Bug Sources

Bugs might be reported by different sources, including Project\'s own
findings (like QA), partner findings, community, or security
researchers. There might be also different ways the Project team learns
about the issue, including Matrix channels, discussion forums etc.
Issues coming from different sources are centralized in the bug tracker,
which also provides an unified identification of all issues.

### Acknowledgement and Bug Triage

After the bug is entered, a developer will perform triage. The process
starts from acknowledging the issue and then consists of verifying all
the information provided by the bug reporter to reproduce the issue. The
developer performing triage might ask additional questions. Then they
assign severity and domain to the issue in the bug tracker. They also
check which versions are affected and might modify the severity level
set by the reporter. Any project member, or the bug reporter, who
disagrees with the assignment might comment on the issue.

If there is a fix available from the reporter, the developer also
verifies if the fix is correct and matches the IP policy. If the fix is
judged acceptable, the process might skip to the Releasing step.

We aim at the first answer of the triage (either finishing triage, or
additional questions to the reporter) in three working days for critical
bugs and seven days for other bugs. In case of a critical bug, the
person performing triage informs the maintainers of the affected
subsystem.

### Prioritizing and Fixing

Bugs with the severity attached enter the prioritization process. It
includes a weekly meeting when the team reviews bugs entered or modified
during the last week: those during the process of triage, and those with
the triage finished. For the bugs with triage finished, the team sets
the priority and might assign it to a developer.

The bug fixes should follow the same contributions guidelines as any
other contribution. The best practice is to develop a fix for the bug in
a separate branch. Fixes for related bugs are possible in the same
branch.

### Releasing

When a bug fix is available in a branch, the developer creates a pull
request. When the change is accepted, it is merged in the main branch.
The developer in charge of the bug verifies with the release manager to
which branches the change should be backported.

If the bug comes from an upstream project, developers upstream the bug
fix. If the upstream is delayed, the Project might ship a local fix.
However, we aim at upstreaming all fixes.

During the time of development of the patch and eventual upstream, the
developer updates the documentation (if appropriate), and adds a
notification to the release notes. Our release notes contain: links to
bugs fixed in the release, links to CVEs fixed in the release (publicly
known) and a list of CVEs fixed that are still under embargo.

If the bug is classified as critical, it might be decided to perform a
separate bugfix release to fix the issue. Otherwise, the bug fix lands
in the next bugfix release.
