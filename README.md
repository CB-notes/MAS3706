<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml" lang="" xml:lang="">
<head>
  <meta charset="utf-8" />
  <meta name="generator" content="pandoc" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes" />
  <title>Week 1: Introduction to Metric spaces</title>
  <style>
    html {
      color: #1a1a1a;
      background-color: #fdfdfd;
    }
    body {
      margin: 0 auto;
      max-width: 36em;
      padding-left: 50px;
      padding-right: 50px;
      padding-top: 50px;
      padding-bottom: 50px;
      hyphens: auto;
      overflow-wrap: break-word;
      text-rendering: optimizeLegibility;
      font-kerning: normal;
    }
    @media (max-width: 600px) {
      body {
        font-size: 0.9em;
        padding: 12px;
      }
      h1 {
        font-size: 1.8em;
      }
    }
    @media print {
      html {
        background-color: white;
      }
      body {
        background-color: transparent;
        color: black;
        font-size: 12pt;
      }
      p, h2, h3 {
        orphans: 3;
        widows: 3;
      }
      h2, h3, h4 {
        page-break-after: avoid;
      }
    }
    p {
      margin: 1em 0;
    }
    a {
      color: #1a1a1a;
    }
    a:visited {
      color: #1a1a1a;
    }
    img {
      max-width: 100%;
    }
    svg {
      height: auto;
      max-width: 100%;
    }
    h1, h2, h3, h4, h5, h6 {
      margin-top: 1.4em;
    }
    h5, h6 {
      font-size: 1em;
      font-style: italic;
    }
    h6 {
      font-weight: normal;
    }
    ol, ul {
      padding-left: 1.7em;
      margin-top: 1em;
    }
    li > ol, li > ul {
      margin-top: 0;
    }
    blockquote {
      margin: 1em 0 1em 1.7em;
      padding-left: 1em;
      border-left: 2px solid #e6e6e6;
      color: #606060;
    }
    code {
      font-family: Menlo, Monaco, Consolas, 'Lucida Console', monospace;
      font-size: 85%;
      margin: 0;
      hyphens: manual;
    }
    pre {
      margin: 1em 0;
      overflow: auto;
    }
    pre code {
      padding: 0;
      overflow: visible;
      overflow-wrap: normal;
    }
    .sourceCode {
     background-color: transparent;
     overflow: visible;
    }
    hr {
      background-color: #1a1a1a;
      border: none;
      height: 1px;
      margin: 1em 0;
    }
    table {
      margin: 1em 0;
      border-collapse: collapse;
      width: 100%;
      overflow-x: auto;
      display: block;
      font-variant-numeric: lining-nums tabular-nums;
    }
    table caption {
      margin-bottom: 0.75em;
    }
    tbody {
      margin-top: 0.5em;
      border-top: 1px solid #1a1a1a;
      border-bottom: 1px solid #1a1a1a;
    }
    th {
      border-top: 1px solid #1a1a1a;
      padding: 0.25em 0.5em 0.25em 0.5em;
    }
    td {
      padding: 0.125em 0.5em 0.25em 0.5em;
    }
    header {
      margin-bottom: 4em;
      text-align: center;
    }
    #TOC li {
      list-style: none;
    }
    #TOC ul {
      padding-left: 1.3em;
    }
    #TOC > ul {
      padding-left: 0;
    }
    #TOC a:not(:hover) {
      text-decoration: none;
    }
    code{white-space: pre-wrap;}
    span.smallcaps{font-variant: small-caps;}
    div.columns{display: flex; gap: min(4vw, 1.5em);}
    div.column{flex: auto; overflow-x: auto;}
    div.hanging-indent{margin-left: 1.5em; text-indent: -1.5em;}
    /* The extra [class] is a hack that increases specificity enough to
       override a similar rule in reveal.js */
    ul.task-list[class]{list-style: none;}
    ul.task-list li input[type="checkbox"] {
      font-size: inherit;
      width: 0.8em;
      margin: 0 0.8em 0.2em -1.6em;
      vertical-align: middle;
    }
  </style>
</head>
<body>
<header id="title-block-header">
<h1 class="title">Week 1: Introduction to Metric spaces</h1>
</header>
<p>Metric spaces were introduced by Fréchet in his PhD dissertation in
1906. The mathematicians of that time were studying various spaces
(mainly spaces of functions) and they had various notions of
<em>convergence</em> in such spaces. For each space its own notion of
convergence was introduced, and studied. Of course, similarities were
noticed and Fréchet realised that these arguments can be unified by
introducing an abstract concept of a <em>metric</em> or <em>distance
function</em>. He could show that many of these spaces were instances of
his new concept of a metric space. Then, by proving one result
axiomatically from the metric axioms, it automatically holds for all
instances.</p>
<p>In the modern view, the concept of a metric space is just an
axiomatisation of the notion of distance. As we will see, different
notions of distance are very important since they occur all the time in
mathematics, statistics and physics. Many geometric objects rely on a
notion of distance (e.g. the unit sphere in
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>ℝ</mi><mi>n</mi></msup><annotation encoding="application/x-tex">\mathbb R^n</annotation></semantics></math>
is exactly the set of points at distance
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mn>1</mn><annotation encoding="application/x-tex">1</annotation></semantics></math>
from the origin). So, it is natural to distill some common properties of
distances in various contexts and set them as axioms.</p>
<p>As already mentioned above, distance plays a fundamental role in the
definition of convergence. Let us recall that definition from
calculus:</p>
<div class="definition">
<p><strong>Definition 1</strong>. Let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mrow><mo stretchy="true" form="prefix">(</mo><msub><mi>x</mi><mi>n</mi></msub><mo stretchy="true" form="postfix">)</mo></mrow><mi>n</mi></msub><annotation encoding="application/x-tex">(x_n)_n</annotation></semantics></math>
be a sequence of real numbers and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>x</mi><mo>∈</mo><mi>ℝ</mi></mrow><annotation encoding="application/x-tex">x\in \mathbb R</annotation></semantics></math>.
Then
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mrow><mo stretchy="true" form="prefix">(</mo><msub><mi>x</mi><mi>n</mi></msub><mo stretchy="true" form="postfix">)</mo></mrow><mi>n</mi></msub><annotation encoding="application/x-tex">(x_n)_n</annotation></semantics></math>
<strong>converges to
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>x</mi><annotation encoding="application/x-tex">x</annotation></semantics></math></strong>,
if for every
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>ε</mi><mo>&gt;</mo><mn>0</mn></mrow><annotation encoding="application/x-tex">\varepsilon&gt;0</annotation></semantics></math>
there exists an
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>N</mi><mo>∈</mo><mi>ℕ</mi></mrow><annotation encoding="application/x-tex">N\in \mathbb{N}</annotation></semantics></math>
such that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="postfix">|</mo><mi>x</mi><mo>−</mo><msub><mi>x</mi><mi>n</mi></msub><mo stretchy="false" form="postfix">|</mo><mo>&lt;</mo><mi>ε</mi></mrow><annotation encoding="application/x-tex">\vert x-x_n\vert&lt;\varepsilon</annotation></semantics></math>
for all
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>≥</mo><mi>N</mi></mrow><annotation encoding="application/x-tex">n\geq N</annotation></semantics></math>.</p>
</div>
<p>In other words: for every error tolerance (the
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>ε</mi><annotation encoding="application/x-tex">\varepsilon</annotation></semantics></math>)
the <em>distance</em> between
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>x</mi><mi>n</mi></msub><annotation encoding="application/x-tex">x_n</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>x</mi><annotation encoding="application/x-tex">x</annotation></semantics></math>
is eventually (i.e. past the the index
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>N</mi><annotation encoding="application/x-tex">N</annotation></semantics></math>)
less than the error tolerance.</p>
<p>Our first goal is to formalise the concept of <em>distance</em>. This
is the content of the following definition:</p>
<div class="definition">
<p><strong>Definition 2</strong>. Let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>X</mi><annotation encoding="application/x-tex">X</annotation></semantics></math>
be a non-empty set. A <strong>metric</strong> (or distance function) on
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>X</mi><annotation encoding="application/x-tex">X</annotation></semantics></math>
is a function
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>d</mi><mo>:</mo><mi>X</mi><mo>×</mo><mi>X</mi><mo>→</mo><mi>ℝ</mi><mo>,</mo><mspace width="0.222em"></mspace><mrow><mo stretchy="true" form="prefix">(</mo><mi>x</mi><mo>,</mo><mi>y</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo>↦</mo><mi>d</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>x</mi><mo>,</mo><mi>y</mi><mo stretchy="true" form="postfix">)</mo></mrow></mrow><annotation encoding="application/x-tex">d \colon X \times X \to \mathbb R, \ (x,y)\mapsto d(x,y)</annotation></semantics></math>
satisfying the following three properties:</p>
<ol>
<li><p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>d</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>x</mi><mo>,</mo><mi>y</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo>=</mo><mn>0</mn></mrow><annotation encoding="application/x-tex">d(x,y) = 0</annotation></semantics></math>
if and only if
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>x</mi><mo>=</mo><mi>y</mi></mrow><annotation encoding="application/x-tex">x=y</annotation></semantics></math>;</p></li>
<li><p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>d</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>x</mi><mo>,</mo><mi>y</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo>=</mo><mi>d</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>y</mi><mo>,</mo><mi>x</mi><mo stretchy="true" form="postfix">)</mo></mrow></mrow><annotation encoding="application/x-tex">d(x,y) = d(y,x)</annotation></semantics></math>
for all
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>x</mi><mo>,</mo><mi>y</mi><mo>∈</mo><mi>X</mi></mrow><annotation encoding="application/x-tex">x,y \in X</annotation></semantics></math>;</p></li>
<li><p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>d</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>x</mi><mo>,</mo><mi>y</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo>≤</mo><mi>d</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>x</mi><mo>,</mo><mi>z</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo>+</mo><mi>d</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>z</mi><mo>,</mo><mi>y</mi><mo stretchy="true" form="postfix">)</mo></mrow></mrow><annotation encoding="application/x-tex">d(x,y) \leq d(x,z) + d(z,y)</annotation></semantics></math>
for all
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>x</mi><mo>,</mo><mi>y</mi><mo>,</mo><mi>z</mi><mo>∈</mo><mi>X</mi></mrow><annotation encoding="application/x-tex">x,y,z \in X</annotation></semantics></math>.</p></li>
</ol>
<p>The pair
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="true" form="prefix">(</mo><mi>X</mi><mo>,</mo><mi>d</mi><mo stretchy="true" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(X,d)</annotation></semantics></math>
is called a <strong>metric space</strong>.</p>
</div>
<p>Let us record a few remarks on the axioms in the definition
above:</p>
<ul>
<li><p>(M1) says that each point has zero distance from itself, and that
distinct points must have a non-zero distance.</p></li>
<li><p>(M2) says that the distance from
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>x</mi><annotation encoding="application/x-tex">x</annotation></semantics></math>
to
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>y</mi><annotation encoding="application/x-tex">y</annotation></semantics></math>
is the same as the distance from
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>y</mi><annotation encoding="application/x-tex">y</annotation></semantics></math>
to
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>x</mi><annotation encoding="application/x-tex">x</annotation></semantics></math>.
We say that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>d</mi><annotation encoding="application/x-tex">d</annotation></semantics></math>
is <strong>symmetric</strong>.</p></li>
<li><p>(M3) is called the <strong>triangle inequality</strong> and gets
its name from the fact that the length of any side of a triangle is at
most the sum of the lengths of the other two sides. It says that a
journey from
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>x</mi><annotation encoding="application/x-tex">x</annotation></semantics></math>
to
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>y</mi><annotation encoding="application/x-tex">y</annotation></semantics></math>
doesn’t get any shorter if you take a detour via
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>z</mi><annotation encoding="application/x-tex">z</annotation></semantics></math>,
but may possibly get longer.</p></li>
<li><p>We can combine the axioms to prove that the distance between any
two points must be non-negative: indeed, for all
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>x</mi><mo>,</mo><mi>y</mi><mo>∈</mo><mi>X</mi></mrow><annotation encoding="application/x-tex">x,y\in X</annotation></semantics></math>
we have
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>2</mn><mi>d</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>x</mi><mo>,</mo><mi>y</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo>=</mo><mi>d</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>x</mi><mo>,</mo><mi>y</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo>+</mo><mi>d</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>x</mi><mo>,</mo><mi>y</mi><mo stretchy="true" form="postfix">)</mo></mrow><mover><mo>=</mo><mrow><mo stretchy="true" form="prefix">(</mo><mi>M</mi><mn>2</mn><mo stretchy="true" form="postfix">)</mo></mrow></mover><mi>d</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>x</mi><mo>,</mo><mi>y</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo>+</mo><mi>d</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>y</mi><mo>,</mo><mi>x</mi><mo stretchy="true" form="postfix">)</mo></mrow><mover><mo>≥</mo><mrow><mo stretchy="true" form="prefix">(</mo><mi>M</mi><mn>3</mn><mo stretchy="true" form="postfix">)</mo></mrow></mover><mi>d</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>x</mi><mo>,</mo><mi>x</mi><mo stretchy="true" form="postfix">)</mo></mrow><mover><mo>=</mo><mrow><mo stretchy="true" form="prefix">(</mo><mi>M</mi><mn>1</mn><mo stretchy="true" form="postfix">)</mo></mrow></mover><mn>0</mn><mo>,</mo></mrow><annotation encoding="application/x-tex">2d(x,y)=d(x,y)+d(x,y)\stackrel{(M2)}{=}d(x,y)+d(y,x)\stackrel{(M3)}{\geq} d(x,x)\stackrel{(M1)}{=}0,</annotation></semantics></math>
so dividing by
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mn>2</mn><annotation encoding="application/x-tex">2</annotation></semantics></math>
gives
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>d</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>x</mi><mo>,</mo><mi>y</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo>≥</mo><mn>0</mn></mrow><annotation encoding="application/x-tex">d(x,y)\geq 0</annotation></semantics></math>.</p></li>
</ul>
<p>Let us now consider some examples:</p>
<div class="example">
<p><strong>Example 3</strong> (Euclidean space). The first example is
the
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>n</mi><annotation encoding="application/x-tex">n</annotation></semantics></math>-dimensional
<strong>Euclidean space</strong>
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="true" form="prefix">(</mo><msup><mi>ℝ</mi><mi>n</mi></msup><mo>,</mo><msub><mi>d</mi><mn>2</mn></msub><mo stretchy="true" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(\mathbb R^n, d_2)</annotation></semantics></math>
where for two points
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>x</mi><mo>=</mo><mrow><mo stretchy="true" form="prefix">(</mo><msub><mi>x</mi><mn>1</mn></msub><mo>,</mo><mi>…</mi><mo>,</mo><msub><mi>x</mi><mi>n</mi></msub><mo stretchy="true" form="postfix">)</mo></mrow></mrow><annotation encoding="application/x-tex">x=(x_1,\ldots, x_n)</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>y</mi><mo>=</mo><mrow><mo stretchy="true" form="prefix">(</mo><msub><mi>y</mi><mn>1</mn></msub><mo>,</mo><mi>…</mi><mo>,</mo><msub><mi>y</mi><mi>n</mi></msub><mo stretchy="true" form="postfix">)</mo></mrow></mrow><annotation encoding="application/x-tex">y=(y_1,\ldots, y_n)</annotation></semantics></math>
in
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>ℝ</mi><mi>n</mi></msup><annotation encoding="application/x-tex">\mathbb R^n</annotation></semantics></math>
we define their <strong>Euclidean distance</strong> by
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>d</mi><mn>2</mn></msub><mrow><mo stretchy="true" form="prefix">(</mo><mi>x</mi><mo>,</mo><mi>y</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo>:=</mo><msqrt><mrow><munderover><mo>∑</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><msup><mrow><mo stretchy="true" form="prefix">(</mo><msub><mi>x</mi><mi>i</mi></msub><mo>−</mo><msub><mi>y</mi><mi>i</mi></msub><mo stretchy="true" form="postfix">)</mo></mrow><mn>2</mn></msup></mrow></msqrt><mi>.</mi></mrow><annotation encoding="application/x-tex">d_2(x,y) := \sqrt{\sum_{i=1}^n (x_i-y_i) ^2}.</annotation></semantics></math></p>
<p>It is easy to see that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="true" form="prefix">(</mo><mi>M</mi><mn>1</mn><mo stretchy="true" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(M1)</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="true" form="prefix">(</mo><mi>M</mi><mn>2</mn><mo stretchy="true" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(M2)</annotation></semantics></math>
are satisfied. To see that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="true" form="prefix">(</mo><mi>M</mi><mn>3</mn><mo stretchy="true" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(M3)</annotation></semantics></math>
holds let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>z</mi><mo>=</mo><mrow><mo stretchy="true" form="prefix">(</mo><msub><mi>z</mi><mn>1</mn></msub><mo>,</mo><mi>…</mi><mo>,</mo><msub><mi>z</mi><mi>n</mi></msub><mo stretchy="true" form="postfix">)</mo></mrow></mrow><annotation encoding="application/x-tex">z=(z_1,\ldots, z_n)</annotation></semantics></math>
be a third point in
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>ℝ</mi><mi>n</mi></msup><annotation encoding="application/x-tex">\mathbb R^n</annotation></semantics></math>.
Then writing out the inequality
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>d</mi><mn>2</mn></msub><mrow><mo stretchy="true" form="prefix">(</mo><mi>x</mi><mo>,</mo><mi>z</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo>≤</mo><msub><mi>d</mi><mn>2</mn></msub><mrow><mo stretchy="true" form="prefix">(</mo><mi>x</mi><mo>,</mo><mi>y</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo>+</mo><msub><mi>d</mi><mn>2</mn></msub><mrow><mo stretchy="true" form="prefix">(</mo><mi>y</mi><mo>,</mo><mi>z</mi><mo stretchy="true" form="postfix">)</mo></mrow></mrow><annotation encoding="application/x-tex">d_2(x,z)\leq d_2(x,y) + d_2(y,z)</annotation></semantics></math>
we have to prove
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msqrt><mrow><munderover><mo>∑</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><msup><mrow><mo stretchy="true" form="prefix">(</mo><msub><mi>x</mi><mi>i</mi></msub><mo>−</mo><msub><mi>z</mi><mi>i</mi></msub><mo stretchy="true" form="postfix">)</mo></mrow><mn>2</mn></msup></mrow></msqrt><mo>≤</mo><msqrt><mrow><munderover><mo>∑</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><msup><mrow><mo stretchy="true" form="prefix">(</mo><msub><mi>x</mi><mi>i</mi></msub><mo>−</mo><msub><mi>y</mi><mi>i</mi></msub><mo stretchy="true" form="postfix">)</mo></mrow><mn>2</mn></msup></mrow></msqrt><mo>+</mo><msqrt><mrow><munderover><mo>∑</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><msup><mrow><mo stretchy="true" form="prefix">(</mo><msub><mi>y</mi><mi>i</mi></msub><mo>−</mo><msub><mi>z</mi><mi>i</mi></msub><mo stretchy="true" form="postfix">)</mo></mrow><mn>2</mn></msup></mrow></msqrt></mrow><annotation encoding="application/x-tex">\sqrt{\sum_{i=1}^n (x_i-z_i) ^2}\leq \sqrt{\sum_{i=1}^n (x_i-y_i) ^2}+\sqrt{\sum_{i=1}^n (y_i-z_i) ^2}</annotation></semantics></math>
To simplify things introduce auxiliary variables
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>r</mi><mi>i</mi></msub><mo>:=</mo><msub><mi>x</mi><mi>i</mi></msub><mo>−</mo><msub><mi>y</mi><mi>i</mi></msub></mrow><annotation encoding="application/x-tex">r_i:=x_i-y_i</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>s</mi><mi>i</mi></msub><mo>:=</mo><msub><mi>y</mi><mi>i</mi></msub><mo>−</mo><msub><mi>z</mi><mi>i</mi></msub></mrow><annotation encoding="application/x-tex">s_i:=y_i-z_i</annotation></semantics></math>.
Plugging these in, the above inequality becomes
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msqrt><mrow><munderover><mo>∑</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><msup><mrow><mo stretchy="true" form="prefix">(</mo><msub><mi>r</mi><mi>i</mi></msub><mo>+</mo><msub><mi>s</mi><mi>i</mi></msub><mo stretchy="true" form="postfix">)</mo></mrow><mn>2</mn></msup></mrow></msqrt><mo>≤</mo><msqrt><mrow><munderover><mo>∑</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><msubsup><mi>r</mi><mi>i</mi><mn>2</mn></msubsup></mrow></msqrt><mo>+</mo><msqrt><mrow><munderover><mo>∑</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><msubsup><mi>s</mi><mi>i</mi><mn>2</mn></msubsup></mrow></msqrt></mrow><annotation encoding="application/x-tex">\sqrt{\sum_{i=1}^n (r_i+s_i) ^2}\leq \sqrt{\sum_{i=1}^n r_i^2}+\sqrt{\sum_{i=1}^n s_i^2}</annotation></semantics></math>
Since both sides arc non-negative, it is equivalent (squaring both
sides) to prove
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><munderover><mo>∑</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><msubsup><mi>r</mi><mi>i</mi><mn>2</mn></msubsup><mo>+</mo><mn>2</mn><munderover><mo>∑</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><msub><mi>r</mi><mi>i</mi></msub><msub><mi>s</mi><mi>i</mi></msub><mo>+</mo><munderover><mo>∑</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><msubsup><mi>s</mi><mi>i</mi><mn>2</mn></msubsup><mo>≤</mo><munderover><mo>∑</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><msubsup><mi>r</mi><mi>i</mi><mn>2</mn></msubsup><mo>+</mo><mn>2</mn><msqrt><mrow><munderover><mo>∑</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><msubsup><mi>r</mi><mi>i</mi><mn>2</mn></msubsup></mrow></msqrt><msqrt><mrow><munderover><mo>∑</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><msubsup><mi>s</mi><mi>i</mi><mn>2</mn></msubsup></mrow></msqrt><mo>+</mo><munderover><mo>∑</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><msubsup><mi>s</mi><mi>i</mi><mn>2</mn></msubsup><mo>,</mo></mrow><annotation encoding="application/x-tex">\sum_{i=1}^n r_i^2 + 2\sum_{i=1}^n r_is_i+ \sum_{i=1}^n s_i^2\leq \sum_{i=1}^n r_i^2+ 2\sqrt{\sum_{i=1}^n r_i^2}\sqrt{\sum_{i=1}^n s_i^2}+\sum_{i=1}^n s_i^2,</annotation></semantics></math>
which we can simplify to
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><munderover><mo>∑</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><msub><mi>r</mi><mi>i</mi></msub><msub><mi>s</mi><mi>i</mi></msub><mo>≤</mo><msqrt><mrow><munderover><mo>∑</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><msubsup><mi>r</mi><mi>i</mi><mn>2</mn></msubsup></mrow></msqrt><msqrt><mrow><munderover><mo>∑</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><msubsup><mi>s</mi><mi>i</mi><mn>2</mn></msubsup></mrow></msqrt><mi>.</mi></mrow><annotation encoding="application/x-tex">\sum_{i=1}^n r_is_i\leq \sqrt{\sum_{i=1}^n r_i^2}\sqrt{\sum_{i=1}^n s_i^2}.</annotation></semantics></math>
Squaring this again we arrive at Cauchy’s inequality
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mrow><mo stretchy="true" form="prefix">(</mo><munderover><mo>∑</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><msub><mi>r</mi><mi>i</mi></msub><msub><mi>s</mi><mi>i</mi></msub><mo stretchy="true" form="postfix">)</mo></mrow><mn>2</mn></msup><mo>≤</mo><mrow><mo stretchy="true" form="prefix">(</mo><munderover><mo>∑</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><msubsup><mi>r</mi><mi>i</mi><mn>2</mn></msubsup><mo stretchy="true" form="postfix">)</mo></mrow><mrow><mo stretchy="true" form="prefix">(</mo><munderover><mo>∑</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><msubsup><mi>s</mi><mi>i</mi><mn>2</mn></msubsup><mo stretchy="true" form="postfix">)</mo></mrow></mrow><annotation encoding="application/x-tex">\left(\sum_{i=1}^n r_is_i\right)^2\leq \left(\sum_{i=1}^n r_i^2\right)\left(\sum_{i=1}^n s_i^2\right)</annotation></semantics></math>
which is known to hold for all
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>n</mi><annotation encoding="application/x-tex">n</annotation></semantics></math>-tuples
of real numbers
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="true" form="prefix">(</mo><msub><mi>r</mi><mn>1</mn></msub><mo>,</mo><mi>…</mi><mo>,</mo><msub><mi>r</mi><mi>n</mi></msub><mo stretchy="true" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(r_1,\ldots, r_n)</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="true" form="prefix">(</mo><msub><mi>s</mi><mn>1</mn></msub><mo>,</mo><mi>…</mi><mo>,</mo><msub><mi>s</mi><mi>n</mi></msub><mo stretchy="true" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(s_1,\ldots, s_n)</annotation></semantics></math>.</p>
</div>
<div class="example">
<p><strong>Example 4</strong>. Besides the Euclidean distance
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>d</mi><mn>2</mn></msub><annotation encoding="application/x-tex">d_2</annotation></semantics></math>
discussed above, there are many other choices of metric we can put on
the
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>n</mi><annotation encoding="application/x-tex">n</annotation></semantics></math>-dimensional
real vector space
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>ℝ</mi><mi>n</mi></msup><annotation encoding="application/x-tex">\mathbb R^n</annotation></semantics></math>.
Let us give two more such examples: for two points
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>x</mi><mo>=</mo><mrow><mo stretchy="true" form="prefix">(</mo><msub><mi>x</mi><mn>1</mn></msub><mo>,</mo><mi>…</mi><mo>,</mo><msub><mi>x</mi><mi>n</mi></msub><mo stretchy="true" form="postfix">)</mo></mrow></mrow><annotation encoding="application/x-tex">x=(x_1,\ldots, x_n)</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>y</mi><mo>=</mo><mrow><mo stretchy="true" form="prefix">(</mo><msub><mi>y</mi><mn>1</mn></msub><mo>,</mo><mi>…</mi><mo>,</mo><msub><mi>y</mi><mi>n</mi></msub><mo stretchy="true" form="postfix">)</mo></mrow></mrow><annotation encoding="application/x-tex">y=(y_1,\ldots, y_n)</annotation></semantics></math>
in
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>ℝ</mi><mi>n</mi></msup><annotation encoding="application/x-tex">\mathbb R^n</annotation></semantics></math>
we define their <strong>taxicab distance</strong>
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>d</mi><mn>1</mn></msub><annotation encoding="application/x-tex">d_1</annotation></semantics></math>
by
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>d</mi><mn>1</mn></msub><mrow><mo stretchy="true" form="prefix">(</mo><mi>x</mi><mo>,</mo><mi>y</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo>:=</mo><munderover><mo>∑</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><mo stretchy="false" form="postfix">|</mo><msub><mi>x</mi><mi>i</mi></msub><mo>−</mo><msub><mi>y</mi><mi>i</mi></msub><mo stretchy="false" form="postfix">|</mo><mi>.</mi></mrow><annotation encoding="application/x-tex">d_1(x,y) := \sum_{i=1}^n \vert x_i-y_i\vert.</annotation></semantics></math></p>
<p>Another metric is the <strong>maximum metric</strong>
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>d</mi><mi>∞</mi></msub><annotation encoding="application/x-tex">d_\infty</annotation></semantics></math>,
which just measures the distance coordinate-wise and then returns the
maximal value:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>d</mi><mi>∞</mi></msub><mrow><mo stretchy="true" form="prefix">(</mo><mi>x</mi><mo>,</mo><mi>y</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo>=</mo><mo>max</mo><mo stretchy="false" form="prefix">{</mo><mo stretchy="false" form="postfix">|</mo><msub><mi>x</mi><mi>i</mi></msub><mo>−</mo><msub><mi>y</mi><mi>i</mi></msub><mo stretchy="false" form="postfix">|</mo><mo>∣</mo><mn>1</mn><mo>≤</mo><mi>i</mi><mo>≤</mo><mi>n</mi><mo stretchy="false" form="postfix">}</mo><mi>.</mi></mrow><annotation encoding="application/x-tex">d_\infty(x,y)=\max\{\vert x_i-y_i\vert\mid 1\leq i\leq n\}.</annotation></semantics></math></p>
</div>
<div class="example">
<p><strong>Example 5</strong>. Let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mo>=</mo><msup><mi>ℂ</mi><mi>n</mi></msup></mrow><annotation encoding="application/x-tex">X=\mathbb C^n</annotation></semantics></math>.
Then we can define a metric on
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>X</mi><annotation encoding="application/x-tex">X</annotation></semantics></math>
by setting
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>d</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>z</mi><mo>,</mo><mi>w</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo>=</mo><msqrt><mrow><munderover><mo>∑</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><mo stretchy="false" form="postfix">|</mo><msub><mi>z</mi><mi>i</mi></msub><mo>−</mo><msub><mi>w</mi><mi>i</mi></msub><msup><mo stretchy="false" form="postfix">|</mo><mn>2</mn></msup></mrow></msqrt></mrow><annotation encoding="application/x-tex">d(z,w)=\sqrt{\sum_{i=1}^n \vert z_i-w_i\vert^2}</annotation></semantics></math>
When we express each entry of the complex tuple in terms of its real and
imaginary parts, the triangle inequality for
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>ℂ</mi><mi>n</mi></msup><annotation encoding="application/x-tex">\mathbb C^n</annotation></semantics></math>
coincides with the one for
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="true" form="prefix">(</mo><msup><mi>ℝ</mi><mrow><mn>2</mn><mi>n</mi></mrow></msup><mo>,</mo><msub><mi>d</mi><mn>2</mn></msub><mo stretchy="true" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(\mathbb R^{2n},d_2)</annotation></semantics></math>
discussed above.</p>
</div>
<div class="example">
<p><strong>Example 6</strong> (Discrete metric). On any set
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mo>≠</mo><mi>∅</mi></mrow><annotation encoding="application/x-tex">X \neq\emptyset</annotation></semantics></math>
the function <span class="math display">$$d(x,y) =
\begin{cases}
    1 &amp; \hbox{ if } x \neq y, \\
    0 &amp; \hbox{ if } x = y
\end{cases}$$</span> defines a metric called the <strong>discrete
metric</strong>. Such ’pathological’ examples, as they are nicknamed,
are not normally used in applications in analysis. They serve as a
warning to check by rigorous proofs that results suggested by intuition
really hold in general metric spaces. In other words, they are potential
counterexamples; they explore the boundaries of the concept of a metric
space.</p>
</div>
<div class="example">
<p><strong>Example 7</strong>. On the complex plane
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>ℂ</mi><annotation encoding="application/x-tex">\mathbb{C}</annotation></semantics></math>
the <span><strong>French Railway metric</strong></span> is given as
<span class="math display">$$d_{f}(z_{1},z_{2})=\begin{cases}
    0 &amp; \hbox{if } z_{1}=z_{2},\\
|z_{1}|+|z_{2}| &amp; \hbox{if } z_{1}\neq z_{2}
\end{cases}$$</span> is a metric (folklore suggests that the shortest
rail journey between any two French towns is via Paris).</p>
</div>
<div class="example">
<p><strong>Example 8</strong> (Metric Subspaces). If
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="true" form="prefix">(</mo><mi>X</mi><mo>,</mo><mi>d</mi><mo stretchy="true" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(X,d)</annotation></semantics></math>
is a metric space and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>Y</mi><mo>⊆</mo><mi>X</mi></mrow><annotation encoding="application/x-tex">Y\subseteq X</annotation></semantics></math>
is a subset of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>X</mi><annotation encoding="application/x-tex">X</annotation></semantics></math>,
then we can define the <strong>induced metric</strong>
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>d</mi><mi>Y</mi></msub><annotation encoding="application/x-tex">d_Y</annotation></semantics></math>
on
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>Y</mi><annotation encoding="application/x-tex">Y</annotation></semantics></math>
as the restriction of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>d</mi><annotation encoding="application/x-tex">d</annotation></semantics></math>
to
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>Y</mi><mo>×</mo><mi>Y</mi><mo>⊆</mo><mi>X</mi><mo>×</mo><mi>X</mi></mrow><annotation encoding="application/x-tex">Y\times Y\subseteq X\times X</annotation></semantics></math>,
i.e.
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>d</mi><mi>Y</mi></msub><mrow><mo stretchy="true" form="prefix">(</mo><mi>x</mi><mo>,</mo><mi>y</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo>=</mo><mi>d</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>x</mi><mo>,</mo><mi>y</mi><mo stretchy="true" form="postfix">)</mo></mrow></mrow><annotation encoding="application/x-tex">d_Y(x,y)=d(x,y)</annotation></semantics></math>
for all
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>x</mi><mo>,</mo><mi>y</mi><mo>∈</mo><mi>Y</mi></mrow><annotation encoding="application/x-tex">x,y\in Y</annotation></semantics></math>.</p>
</div>
<p>If these were the only examples of metric spaces it is doubtful
whether general metric space theory would be worthwhile. The examples
below indicate the wide range of metric space theory (but do not exhaust
it).</p>
<div class="example">
<p><strong>Example 9</strong>. The following metric plays an important
role in number theory. Let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>p</mi><annotation encoding="application/x-tex">p</annotation></semantics></math>
be a fixed prime number. Define a metric
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>d</mi><mi>p</mi></msub><mo>:</mo><mi>ℤ</mi><mo>×</mo><mi>ℤ</mi><mo>→</mo><mi>ℝ</mi></mrow><annotation encoding="application/x-tex">d_p:\mathbb Z\times \mathbb Z\to \mathbb R</annotation></semantics></math>
by setting
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>d</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>m</mi><mo>,</mo><mi>m</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo>=</mo><mn>0</mn></mrow><annotation encoding="application/x-tex">d(m,m)=0</annotation></semantics></math>
and for
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>≠</mo><mi>m</mi></mrow><annotation encoding="application/x-tex">n\neq m</annotation></semantics></math>
set
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>d</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>m</mi><mo>,</mo><mi>n</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo>=</mo><mn>1</mn><mi>/</mi><mi>r</mi></mrow><annotation encoding="application/x-tex">d(m,n)=1/r</annotation></semantics></math>
where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>p</mi><mrow><mi>r</mi><mo>−</mo><mn>1</mn></mrow></msup><annotation encoding="application/x-tex">p^{r-1}</annotation></semantics></math>
is the highest power of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>p</mi><annotation encoding="application/x-tex">p</annotation></semantics></math>
which divides
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>m</mi><mo>−</mo><mi>n</mi></mrow><annotation encoding="application/x-tex">m-n</annotation></semantics></math>.</p>
</div>
<div class="example">
<p><strong>Example 10</strong> (The word metric on a finitely generated
group). This example will only make sense if you know about groups and
generating sets. Suppose
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>G</mi><annotation encoding="application/x-tex">G</annotation></semantics></math>
is a finitely generated group and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>S</mi><annotation encoding="application/x-tex">S</annotation></semantics></math>
is a generating set for
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>G</mi><annotation encoding="application/x-tex">G</annotation></semantics></math>.
That is every element
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>g</mi><mo>∈</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">g\in G</annotation></semantics></math>
can be written as a product
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>g</mi><mo>=</mo><msub><mi>g</mi><mn>1</mn></msub><mi>⋯</mi><msub><mi>g</mi><mi>n</mi></msub></mrow><annotation encoding="application/x-tex">g=g_1\cdots g_n</annotation></semantics></math>
of elements in
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>S</mi><annotation encoding="application/x-tex">S</annotation></semantics></math>
(and their inverses). The shortest way to write
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>g</mi><annotation encoding="application/x-tex">g</annotation></semantics></math>
in this way is called the length of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>g</mi><annotation encoding="application/x-tex">g</annotation></semantics></math>,
denoted by
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>l</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>g</mi><mo stretchy="true" form="postfix">)</mo></mrow></mrow><annotation encoding="application/x-tex">l(g)</annotation></semantics></math>.
Now we can define the word-metric on
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>G</mi><annotation encoding="application/x-tex">G</annotation></semantics></math>
by setting
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>d</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>g</mi><mo>,</mo><mi>h</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo>=</mo><mi>l</mi><mrow><mo stretchy="true" form="prefix">(</mo><msup><mi>g</mi><mrow><mi>−</mi><mn>1</mn></mrow></msup><mi>h</mi><mo stretchy="true" form="postfix">)</mo></mrow><mi>.</mi></mrow><annotation encoding="application/x-tex">d(g,h)=l(g^{-1}h).</annotation></semantics></math></p>
</div>
<div class="example">
<p><strong>Example 11</strong> (Geodesic distance on a graph). Let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="true" form="prefix">(</mo><mi>V</mi><mo>,</mo><mi>E</mi><mo stretchy="true" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(V,E)</annotation></semantics></math>
be a connected graph (undirected, without multiple edges between
vertices), with vertex set
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>V</mi><annotation encoding="application/x-tex">V</annotation></semantics></math>
and edge set
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>E</mi><annotation encoding="application/x-tex">E</annotation></semantics></math>.
Then we can define a metric on
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>V</mi><annotation encoding="application/x-tex">V</annotation></semantics></math>
by letting
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>d</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>v</mi><mo>,</mo><mi>w</mi><mo stretchy="true" form="postfix">)</mo></mrow></mrow><annotation encoding="application/x-tex">d(v,w)</annotation></semantics></math>
be the length of the shortest path between the two vertices
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>v</mi><annotation encoding="application/x-tex">v</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>w</mi><annotation encoding="application/x-tex">w</annotation></semantics></math>.
This metric is important in the study of networks.</p>
</div>
<div class="example">
<p><strong>Example 12</strong> (Hamming distance). Let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>Σ</mi><mo>=</mo><mo stretchy="false" form="prefix">{</mo><mi>a</mi><mo>,</mo><mi>b</mi><mo>,</mo><mi>c</mi><mo>,</mo><mi>…</mi><mo>,</mo><mi>z</mi><mo stretchy="false" form="postfix">}</mo></mrow><annotation encoding="application/x-tex">\Sigma=\{a,b,c,\ldots, z\}</annotation></semantics></math>
be the modern Latin alphabet. Let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>X</mi><annotation encoding="application/x-tex">X</annotation></semantics></math>
be the set of all strings of letters in
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>Σ</mi><annotation encoding="application/x-tex">\Sigma</annotation></semantics></math>
of length 4 (e.g.
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>a</mi><mi>b</mi><mi>c</mi><mi>d</mi></mrow><annotation encoding="application/x-tex">abcd</annotation></semantics></math>
is an element in
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>X</mi><annotation encoding="application/x-tex">X</annotation></semantics></math>,
so are
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>m</mi><mi>a</mi><mi>t</mi><mi>h</mi></mrow><annotation encoding="application/x-tex">math</annotation></semantics></math>
or
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>i</mi><mi>o</mi><mi>s</mi><mi>k</mi></mrow><annotation encoding="application/x-tex">iosk</annotation></semantics></math>).
The <strong>Hamming distance</strong>
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>d</mi><mi>H</mi></msub><annotation encoding="application/x-tex">d_H</annotation></semantics></math>
between two strings in
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>X</mi><annotation encoding="application/x-tex">X</annotation></semantics></math>
is the number of positions at which the corresponding symbols are
different. In other words, it measures the minimum number of
substitutions required to change one string into the other. One can
check that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>d</mi><mi>H</mi></msub><annotation encoding="application/x-tex">d_H</annotation></semantics></math>
is indeed a metric on
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>X</mi><annotation encoding="application/x-tex">X</annotation></semantics></math>.
A major application of the Hamming distance is in coding theory.</p>
</div>
<p>Let us now also introduce a couple of the <em>function spaces</em>
that motivated Fréchet to study metric spaces in the first place. These
will be studied in much more detail in Linear Analysis, so we keep our
discussion here brief.</p>
<div class="example">
<p><strong>Example 13</strong> (Uniform metric). Let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>A</mi><mo>≠</mo><mi>∅</mi></mrow><annotation encoding="application/x-tex">A\neq \emptyset</annotation></semantics></math>
be a set. A function
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>f</mi><mo>:</mo><mi>A</mi><mo>→</mo><mi>ℝ</mi></mrow><annotation encoding="application/x-tex">f:A\rightarrow \mathbb R</annotation></semantics></math>
is called <strong>bounded</strong>, if there exists a constant
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>C</mi><mo>&gt;</mo><mn>0</mn></mrow><annotation encoding="application/x-tex">C&gt;0</annotation></semantics></math>
such that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="postfix">|</mo><mi>f</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>a</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo stretchy="false" form="postfix">|</mo><mo>≤</mo><mi>C</mi></mrow><annotation encoding="application/x-tex">\vert f(a)\vert\leq C</annotation></semantics></math>
for all
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>a</mi><mo>∈</mo><mi>A</mi></mrow><annotation encoding="application/x-tex">a\in A</annotation></semantics></math>.
Let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mo>ℓ</mo><mi>∞</mi></msup><mrow><mo stretchy="true" form="prefix">(</mo><mi>A</mi><mo stretchy="true" form="postfix">)</mo></mrow></mrow><annotation encoding="application/x-tex">\ell^\infty (A)</annotation></semantics></math>
denote the set of all such bounded, complex valued functions on
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>A</mi><annotation encoding="application/x-tex">A</annotation></semantics></math>.
Then for
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>f</mi><mo>,</mo><mi>g</mi><mo>∈</mo><msup><mo>ℓ</mo><mi>∞</mi></msup><mrow><mo stretchy="true" form="prefix">(</mo><mi>A</mi><mo stretchy="true" form="postfix">)</mo></mrow></mrow><annotation encoding="application/x-tex">f,g\in \ell^\infty(A)</annotation></semantics></math>
we can define
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>d</mi><mi>∞</mi></msub><mrow><mo stretchy="true" form="prefix">(</mo><mi>f</mi><mo>,</mo><mi>g</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo>:=</mo><munder><mo>sup</mo><mrow><mi>a</mi><mo>∈</mo><mi>A</mi></mrow></munder><mo stretchy="false" form="postfix">|</mo><mi>f</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>a</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo>−</mo><mi>g</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>a</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo stretchy="false" form="postfix">|</mo><mi>.</mi></mrow><annotation encoding="application/x-tex">d_\infty(f,g) := \sup_{a\in A} \vert f(a)-g(a)\vert.</annotation></semantics></math>
We leave it as an exercise to show that this is indeed a metric.</p>
</div>
<div class="example">
<p><strong>Example 14</strong>
(<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>L</mi><mn>1</mn></msup><annotation encoding="application/x-tex">L^1</annotation></semantics></math>
metric). Let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>C</mi><mrow><mo stretchy="true" form="prefix">[</mo><mi>a</mi><mo>,</mo><mi>b</mi><mo stretchy="true" form="postfix">]</mo></mrow></mrow><annotation encoding="application/x-tex">C[a,b]</annotation></semantics></math>
denote the set of all continuous functions
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>f</mi><mo>:</mo><mrow><mo stretchy="true" form="prefix">[</mo><mi>a</mi><mo>,</mo><mi>b</mi><mo stretchy="true" form="postfix">]</mo></mrow><mo>→</mo><mi>ℝ</mi></mrow><annotation encoding="application/x-tex">f:[a,b]\to \mathbb R</annotation></semantics></math>.
Then we can define a metric
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>d</mi><mn>1</mn></msub><annotation encoding="application/x-tex">d_1</annotation></semantics></math>
on
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>C</mi><mrow><mo stretchy="true" form="prefix">[</mo><mi>a</mi><mo>,</mo><mi>b</mi><mo stretchy="true" form="postfix">]</mo></mrow></mrow><annotation encoding="application/x-tex">C[a,b]</annotation></semantics></math>
by setting
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>d</mi><mn>1</mn></msub><mrow><mo stretchy="true" form="prefix">(</mo><mi>f</mi><mo>,</mo><mi>g</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo>:=</mo><msubsup><mo>∫</mo><mi>a</mi><mi>b</mi></msubsup><mo stretchy="false" form="postfix">|</mo><mi>f</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>x</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo>−</mo><mi>g</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>x</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo stretchy="false" form="postfix">|</mo><mspace width="0.222em"></mspace><mi mathvariant="normal">d</mi><mi>x</mi><mi>.</mi></mrow><annotation encoding="application/x-tex">d_1(f,g):=\int_a^b \vert f(x)-g(x)\vert \ \mathrm d x.</annotation></semantics></math></p>
</div>
<div class="example">
<p><strong>Example 15</strong>
(<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>L</mi><mn>2</mn></msup><annotation encoding="application/x-tex">L^2</annotation></semantics></math>
metric). Let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>C</mi><mrow><mo stretchy="true" form="prefix">[</mo><mi>a</mi><mo>,</mo><mi>b</mi><mo stretchy="true" form="postfix">]</mo></mrow></mrow><annotation encoding="application/x-tex">C[a,b]</annotation></semantics></math>
denote the set of all continuous functions
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>f</mi><mo>:</mo><mrow><mo stretchy="true" form="prefix">[</mo><mi>a</mi><mo>,</mo><mi>b</mi><mo stretchy="true" form="postfix">]</mo></mrow><mo>→</mo><mi>ℝ</mi></mrow><annotation encoding="application/x-tex">f:[a,b]\to \mathbb R</annotation></semantics></math>.
Then we can define a metric
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>d</mi><mn>2</mn></msub><annotation encoding="application/x-tex">d_2</annotation></semantics></math>
on
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>C</mi><mrow><mo stretchy="true" form="prefix">[</mo><mi>a</mi><mo>,</mo><mi>b</mi><mo stretchy="true" form="postfix">]</mo></mrow></mrow><annotation encoding="application/x-tex">C[a,b]</annotation></semantics></math>
by setting
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>d</mi><mn>2</mn></msub><mrow><mo stretchy="true" form="prefix">(</mo><mi>f</mi><mo>,</mo><mi>g</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo>:=</mo><msup><mrow><mo stretchy="true" form="prefix">(</mo><msubsup><mo>∫</mo><mi>a</mi><mi>b</mi></msubsup><msup><mrow><mo stretchy="true" form="prefix">(</mo><mi>f</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>x</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo>−</mo><mi>g</mi><mrow><mo stretchy="true" form="prefix">(</mo><mi>x</mi><mo stretchy="true" form="postfix">)</mo></mrow><mo stretchy="true" form="postfix">)</mo></mrow><mn>2</mn></msup><mspace width="0.222em"></mspace><mi mathvariant="normal">d</mi><mi>x</mi><mo stretchy="true" form="postfix">)</mo></mrow><mfrac><mn>1</mn><mn>2</mn></mfrac></msup><mi>.</mi></mrow><annotation encoding="application/x-tex">d_2(f,g):=\left( \int_a^b (f(x)-g(x))^2 \ \mathrm d x\right)^\frac{1}{2}.</annotation></semantics></math></p>
</div>
</body>
</html>
