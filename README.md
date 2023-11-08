# spotbugs-spring-boot-filter-repro

Requires Java 17.

Run SpotBugs:

```shell
./gradlew spotbugsMain
```

It will fail with:

```shell
> Task :spotbugsMain FAILED
Exception in thread "main" java.lang.NoSuchMethodError: 'org.apache.commons.lang3.Range org.apache.commons.lang3.Range.of(java.lang.Comparable, java.lang.Comparable)'
        at org.apache.commons.text.translate.NumericEntityEscaper.<init>(NumericEntityEscaper.java:97)
        at org.apache.commons.text.translate.NumericEntityEscaper.between(NumericEntityEscaper.java:59)
        at org.apache.commons.text.StringEscapeUtils.<clinit>(StringEscapeUtils.java:271)
        at edu.umd.cs.findbugs.util.Strings.unescapeXml(Strings.java:295)
        at edu.umd.cs.findbugs.SAXBugCollectionHandler.getRequiredAttribute(SAXBugCollectionHandler.java:804)
        at edu.umd.cs.findbugs.SAXBugCollectionHandler.parseMatcher(SAXBugCollectionHandler.java:452)
        at edu.umd.cs.findbugs.SAXBugCollectionHandler.startElement(SAXBugCollectionHandler.java:340)
        at java.xml/com.sun.org.apache.xerces.internal.parsers.AbstractSAXParser.startElement(AbstractSAXParser.java:518)
        at java.xml/com.sun.org.apache.xerces.internal.parsers.AbstractXMLDocumentParser.emptyElement(AbstractXMLDocumentParser.java:183)
        at java.xml/com.sun.org.apache.xerces.internal.impl.XMLDocumentFragmentScannerImpl.scanStartElement(XMLDocumentFragmentScannerImpl.java:1387)
        at java.xml/com.sun.org.apache.xerces.internal.impl.XMLDocumentFragmentScannerImpl$FragmentContentDriver.next(XMLDocumentFragmentScannerImpl.java:2726)
        at java.xml/com.sun.org.apache.xerces.internal.impl.XMLDocumentScannerImpl.next(XMLDocumentScannerImpl.java:605)
        at java.xml/com.sun.org.apache.xerces.internal.impl.XMLDocumentFragmentScannerImpl.scanDocument(XMLDocumentFragmentScannerImpl.java:542)
        at java.xml/com.sun.org.apache.xerces.internal.parsers.XML11Configuration.parse(XML11Configuration.java:889)
        at java.xml/com.sun.org.apache.xerces.internal.parsers.XML11Configuration.parse(XML11Configuration.java:825)
        at java.xml/com.sun.org.apache.xerces.internal.parsers.XMLParser.parse(XMLParser.java:141)
        at java.xml/com.sun.org.apache.xerces.internal.parsers.AbstractSAXParser.parse(AbstractSAXParser.java:1224)
        at java.xml/com.sun.org.apache.xerces.internal.jaxp.SAXParserImpl$JAXPSAXParser.parse(SAXParserImpl.java:637)
        at edu.umd.cs.findbugs.filter.Filter.parse(Filter.java:234)
        at edu.umd.cs.findbugs.filter.Filter.parse(Filter.java:208)
        at edu.umd.cs.findbugs.filter.Filter.<init>(Filter.java:133)
        at edu.umd.cs.findbugs.FindBugs.configureFilter(FindBugs.java:471)
        at edu.umd.cs.findbugs.FindBugs2.addFilter(FindBugs2.java:404)
        at edu.umd.cs.findbugs.FindBugs2.configureFilters(FindBugs2.java:551)
        at edu.umd.cs.findbugs.FindBugs2.setUserPreferences(FindBugs2.java:505)
        at edu.umd.cs.findbugs.TextUICommandLine.configureEngine(TextUICommandLine.java:723)
        at edu.umd.cs.findbugs.FindBugs.processCommandLine(FindBugs.java:359)
        at edu.umd.cs.findbugs.FindBugs2.main(FindBugs2.java:1221)
```

Edit `gradle.properties` and change `spotbugsVersion` to `4.8.0` and re-run SpotBugs, the build will pass.
