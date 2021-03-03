# Visit https://github.com/lowlighter/metrics/blob/master/action.yml for full reference
name: Metrics
on:
  # Schedule updates (each hour)
  schedule: [{cron: "0 * * * *"}]
  # Lines below let you run workflow manually and on each commit
  push: {branches: ["master", "main"]}
  workflow_dispatch:
jobs:
  github-metrics:
    runs-on: ubuntu-latest
    steps:
      - uses: lowlighter/metrics@latest
        with:
          # Your GitHub token
          token: ${{ secrets.METRICS_TOKEN }}
          # GITHUB_TOKEN is a special auto-generated token restricted to current repository, which is used to push files in it
          committer_token: ${{ secrets.GITHUB_TOKEN }}

          # Options
          user: PoweredByWard
          template: classic
          base: header, activity, community, repositories, metadata
          config_timezone: Europe/Brussels
          plugin_activity: yes
          plugin_activity_days: 14
          plugin_activity_filter: all
          plugin_activity_limit: 5
          plugin_activity_timestamps: yes
          plugin_activity_visibility: all
          plugin_followup: yes
          plugin_gists: yes
          plugin_introduction: yes
          plugin_introduction_title: yes
          plugin_isocalendar: yes
          plugin_isocalendar_duration: half-year
          plugin_languages: yes
          plugin_languages_colors: github
          plugin_languages_threshold: 0%
          plugin_lines: yes
          plugin_pagespeed: yes
          plugin_pagespeed_detailed: yes
          plugin_pagespeed_screenshot: yes
          plugin_pagespeed_url: .user.website
          plugin_people: yes
          plugin_people_limit: 28
          plugin_people_size: 28
          plugin_people_types: followers, following
          plugin_stars: yes
          plugin_stars_limit: 4
          plugin_tweets: yes
          plugin_tweets_limit: 2
          plugin_tweets_user: .user.twitter
