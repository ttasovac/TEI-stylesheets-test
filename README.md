# Testing TEI Stylesheets

This repo consists of:

- an odd file called `test.odd`
- an oXygen project file `testProject.xpr`, which defines two transformation scenarios:
  - `TEI ODD XHTML - Copy of oXygen Transformation Scenario`
  - `TEI ODD XHTML - Using wrapper xsl file`
- `wrapper.xsl`

The wrapper file replicates the oXygen transformation scenario using `<xsl:import>` rules and one `<xsl:param>` like this:

```xml
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
    xmlns:tei="http://www.tei-c.org/ns/1.0" xmlns:teix="http://www.tei-c.org/ns/Examples"
    xpath-default-namespace="http://www.tei-c.org/ns/1.0" version="2.0"
    exclude-result-prefixes="tei teix">

    <xsl:import href="https://tei-c.org/release/xml/tei/stylesheet/odds/odd2odd.xsl"/>
    <xsl:import href="https://tei-c.org/release/xml/tei/stylesheet/odds/odd2lite.xsl"/>
    <xsl:import href="https://tei-c.org/release/xml/tei/stylesheet/html/html.xsl"/>

    <xsl:param name="defaultSource">https://tei-c.org/release/xml/tei/odd/p5subset.xml</xsl:param>

</xsl:stylesheet>
```

The output of the default and the wrapped transformation scenarios should be the same.

## oXygen Transformation Scenario

The default oXygen scenario produces `test.fromOxygenScenario.html` which looks as it should:

![Скриншот 2020-05-12 09.49.41](https://i.imgur.com/HARgChO.png)

## Transformation using a wrapper file

The wrapped scenario produces `test.withWrapper.html` which in its entirety like this:

![Скриншот 2020-05-12 09.51.59](https://i.imgur.com/a7yCtBK.png)

As you can see, the schemaSpec doesn't get properly converted to html.

All this happens using oXygen 22.0, build 2020030607.
