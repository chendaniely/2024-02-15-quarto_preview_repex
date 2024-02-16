# Repex for quarto preview and image rendering

If you open `this_works.qmd` and click the preview button in VSCode or Render button in RStudio,
the resulting html file in the viewer pane and output html render as expected.

If you open the `analysis/no_work.qmd` file and click the preview or render button,
you get a broken image link and also you see this in the VSCode terminal:

```shell
% quarto preview /Users/danielchen/temp/quarto_fig_test/analysis/no_work.qmd --no-browser --no-watch-inputs


processing file: no_work.qmd
1/4 [unnamed-chunk-1]
2/4
3/4 [unnamed-chunk-2]
4/4
output file: no_work.knit.md

pandoc
  to: html
  output-file: no_work.html
  standalone: true
  section-divs: true
  html-math-method: mathjax
  wrap: none
  default-image-extension: png

metadata
  document-css: false
  link-citations: true
  date-format: long
  lang: en

Output created: no_work.html

Watching files for changes
Browse at http://localhost:7423/
  /output/fig_dir.png (404: Not Found)
```

to fix this,
you need to create a top-level `_quarto.yml` file to turn the entire folder into a quarto project.

```shell
touch _quarto.yml
```

If you just re-preview or re-render the document, you will still have a broken link,
you need to fully restart the session (ctrl+c) and try again.
This will have the html preview work as expected.
