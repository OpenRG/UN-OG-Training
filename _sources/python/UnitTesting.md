(Chap_UnitTesting)=
# Unit Testing

As a code base expands and the scripts and modules become more interdependent and interconnected, the probability increases that additions to the code will introduce bugs. And as the code base becomes bigger, the harder it can be to find bugs. One of the primary ways to protect the functionality of a code base from bugs is unit testing.


(SecUnitTestPytest)=
## PyTest

Testing of your source code is important to ensure that the results of your code are accurate and to cut down on debugging time.  Fortunately, `Python` has a nice suite of tools for unit testing. In this section, we will introduce the `pytest` package and show how to use it to test your code.

The iframe below contains a PDF of the BYU ACME open-access lab entitled, "[Unit Testing](https://drive.google.com/file/d/1109ci_tqZz30C2ymf0Hs3UO66l865U0-/view?usp=sharing)". You can either scroll through the lab on this page using the iframe window, or you can download the PDF for use on your computer. See {cite}`BYUACME_UnitTest`. {numref}`ExerTest-acme` below has you work through the problems in this BYU ACME lab. Two Python scripts ([`specs.py`](https://github.com/OpenRG/UN-OG-Training/tree/main/code/UnitTest/specs.py) and [`test_specs.py`](https://github.com/OpenRG/UN-OG-Training/tree/main/code/UnitTest/test_specs.py)) used in the lab are stored in the [`./code/UnitTest/`](https://github.com/OpenRG/UN-OG-Training/tree/main/code/UnitTest) directory.

<div>
  <iframe id="inlineFrameExample"
      title="Inline Frame Example"
      width="100%"
      height="700"
      src="https://drive.google.com/file/d/1109ci_tqZz30C2ymf0Hs3UO66l865U0-/preview?usp=sharing">
  </iframe>
</div>


(SecUnitTestCodecov)=
## Code coverage

Put section here on code coverage.


(SecUnitTestGHActions)=
## Continuous integration testing and GitHub Actions

Put section here on GitHub Actions and continuous integration.


(SecUnitTestExercises)=
## Exercises

```{exercise-start}
:label: ExerTest-acme
:class: green
```
Read the BYU ACME "[Unit Testing](https://drive.google.com/file/d/1109ci_tqZz30C2ymf0Hs3UO66l865U0-/view?usp=sharing)" lab and complete Problems 1 through 6 in the lab. {cite}`BYUACME_UnitTest`
```{exercise-end}
```

```{exercise-start}
:label: ExerTest-assert_value
```
Take simple function to minimize from SciPy and write a unit test for it (know analytic solutions so can test that SciPy is working correctly)
```{exercise-end}
```

```{exercise-start}
:label: ExerTest-assert_type
```
Another single test where assert that object a certain type
```{exercise-end}
```

```{exercise-start}
:label: ExerTest-parameterize
```
Use the `@pytest.mark.parametrize` decorator to test a function for multiple inputs
```{exercise-end}
```

```{exercise-start}
:label: ExerTest-markers
```
Use pytest markers to skip a test
```{exercise-end}
```

```{exercise-start}
:label: ExerTest-???
```
Something else... Maybe a test that checks if an exception if raised?
```{exercise-end}
```
