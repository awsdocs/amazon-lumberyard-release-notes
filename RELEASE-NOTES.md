# Contributing to the Lumberyard Public Release Notes

The Amazon Lumberyard (beta) Release Notes are formed and managed on Github in this repo (https://github.com/awsdocs/amazon-lumberyard-release-notes). Release Notes for the coming version are in a formative state and are provided as early information as to the state of the release; they do **not** represent a commitment for delivery in the final release version. We develop these in public to give customers an early look into what we know about a coming release and to centralize our Release Notes development process. 

All past Release Notes are archived here as well.

Anyone can contribute to these Release Notes with a pull request.  The Amazon Lumberyard Docs Team will review all PRs within 5 business days of submission. Amazon Lumberyard reserves the right to reject any Release Notes contribution for any reason.

You can also provide feedback by submitting Issues. As with PRs, we will respond to PRs within 5 business days of submission. We invite you to use this repo as a formal channel of communication with the Lumberyard team around releases.

This is a public repo and all branches are visible. If you need to make private changes, please fork this repo to your own GitHub account, and then submit a PR to this repo from your fork when the content is ready for public visibility.

## Lumberyard Public Release Notes Structure

The Release Notes are structured under two folders:
  - '/coming-release' -- this contains the developing Release Notes for the **next** release. 
  - '/archive' -- this contains an archive of prior publically sourced Release Notes, organized by release version number. (For example, '/archive/1.21'.)

Under the '/coming-release' folder or a version-numbered folder under '/archive', you'll find 4 MarkDown files:
  - 'index.md': Authored by the Lumberyard team at the time of release. This file contains the highlighted changes for the release and links to the other pages in a release's Release Notes.
  - 'fixes.md': A comprehensive list of fixes to Lumberyard for a release.
  - 'chamges-improvements.md': A list of all significant changes and improvements made to Lumberyard for a specific release.
  - 'known-issues.md': Updated list of known bugs, problems, and issues with Lumberyard as of the specific release. Please contribute to this list and keep it up-to-date!

## Lumberyard Public Release Notes Workflow

When a new release is started, the Lumberyard team will move the last release's Release Notes into the '/archive' folder and copy the templates over from the '/templates' folder into the '/coming-release' folder. Be sure to remove the "-template" portion of the file name.

**NOTE**: Do NOT specify the version number or date(s) until the day of the release. Use "the next version of the Amazon Lumberyard beta" instead to replace any placeholder values for version numbers or dates. All PRs that affect topics in the 'coming-release' folder will be rejected if they specify a date or version number before the release date itself.

Finally, copy the Known Issues (known-issues.md) from the prior release into /coming-release/known-issues.md. This is because Known Issues carry over, and we will remove them as they are addressed to keep a rolling record of customer-facing bugs, problems, and issues.



