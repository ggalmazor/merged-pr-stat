# merged-pr-stat
This is a tool to creates merged PullRequest statistics.  It is useful to measure the productivity and health of your team.

## Installation
```
$ npm install -g shibayu36/merged-pr-stat
```

## Usage
The following command aggregates PullRequests of microsoft/vscode and microsoft/TypesScript which merged between `--start` and `--end`.  You can filter PullRequests by `--query` option.  See also https://docs.github.com/en/github/searching-for-information-on-github/searching-issues-and-pull-requests if you want to know what you can specify for `--query`

```
$ GITHUB_TOKEN=... merged-pr-stat --start=2020-07-01T00:00:00 --end=2020-07-30T23:59:59 --query="repo:microsoft/vscode repo:microsoft/TypeScript"
```

output is

```json
{
  "count": 258,
  "authorCount": 77,
  "additionsAverage": 107.89147286821705,
  "additionsMedian": 19,
  "deletionsAverage": 41.97286821705426,
  "deletionsMedian": 3,
  "leadTimeSecondsAverage": 578271,
  "leadTimeSecondsMedian": 58163,
  "timeToMergeSecondsAverage": 735697,
  "timeToMergeSecondsMedian": 82453
}
```

* count: the number of merged PullRequests
* authorCount: the number of author who creates PullRequests
* additionsAverage: the average of number of added lines
* additionsMedian: the median of number of added lines
* deletionsAverage: the average of number of deleted lines
* deletionsMedian: the median of number of deleted lines
* leadTimeSecondsAverage: the average of seconds between a PullRequest created and a PullRequest merged
* leadTimeSecondsMedian: the median of seconds between a PullRequest created and a PullRequest merged
* timeToMergeSecondsAverage: the average of seconds between a first commit date and a PullRequest merged date

If you want to know about leadTime and timeToMerge for details, See https://sourcelevel.io/blog/5-metrics-engineering-managers-can-extract-from-pull-requests
