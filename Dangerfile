# Make it more obvious that a PR is a work in progress and shouldn't be merged yet
warn("PR is classed as Work in Progress") if github.pr_title.include? "[WIP]"

# Warn when there is a big PR
warn("Big PR") if git.lines_of_code > 500

# Lint
swiftlint.lint_files inline_mode: true

# Warn when library files has been updated but not tests.
tests_updated = !git.modified_files.grep(/Tests/).empty?
if has_app_changes && !tests_updated
  warn("The library files were changed, but the tests remained unmodified. Consider updating or adding to the tests to match the library changes.")
end

# Mainly to encourage writing up some reasoning about the PR, rather than
# just leaving a title
if github.pr_body.length < 5
  fail "Please provide a summary in the Pull Request description"
end


