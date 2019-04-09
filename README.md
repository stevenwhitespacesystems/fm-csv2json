<!-- PROJECT LOGO -->
<br />
<p align="center">
  <a href="https://github.com/stevenwhitespacesystems/fm-csv2json">
    <img src="logo-alt.png" alt="Logo" width="140" height="104">
  </a>

  <h3 align="center">fm-csv2json</h3>

  <p align="center">
    An XML Parser that converts XML into JSON on the FileMaker Pro Platform.
    <br />
    <a href="https://github.com/stevenwhitespacesystems/fm-csv2json"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/stevenwhitespacesystems/fm-csv2json/issues">Report Bug</a>
    ·
    <a href="https://github.com/stevenwhitespacesystems/fm-csv2json/issues">Request Feature</a>
  </p>
</p>

<!-- PROJECT SHIELDS -->
[![FileMaker Version][filemaker-shield]]()
[![FileMaker Platform][platform-shield]]()
[![Commit Shield][commit-shield]]()
[![Contributors][contributors-shield]]()
[![MIT License][license-shield]][license-url]
[![Facebook][facebook-shield]][facebook-url]
[![LinkedId][linkedin-shield]][linkedin-url]

<!-- TABLE OF CONTENTS -->
## Table of Contents

* [About the Project](#about-the-project)
  * [Built With](#built-with)
* [Features](#features)
* [Getting Started](#getting-started)
  * [Prerequisites](#prerequisites)
    * [Version](#version)
    * [Custom Functions](#custom-functions)
    * [Limitations](#limitations)
* [Usage](#usage)
  * [Installation](#installation)
  * [Quick Start](#quick-start)
  * [Required Parameters](#required-parameters)
* [Contributing](#contributing)
* [License](#license)
* [Contact](#contact)
* [Acknowledgements](#acknowledgements)
* [fmapi Product Suite](#fmapi-product-suite)
  * [fmapi Apps](#fmapi-apps)

<!-- ABOUT THE PROJECT -->
## About The Project

<p align="center">
  <a href="https://github.com/stevenwhitespacesystems/fm-csv2json">
    <img src="logo.png" alt="Logo" width="580" height="208">
  </a>
</p>

I was browsing over at the FileMaker forums and came across a question about parsing CSV data.

This got caught our interest and made us ask the question.

> Could we take some CSV data and transform it into a valid JSON Object?

We present `fm-csv2json`.

A FileMaker script which when passed a **valid** CSV string, will covert this string into a JSON object.

### Built With
* [FileMaker Pro](https://www.filemaker.com/)
* No 3rd party plugins.

<!-- FEATURES -->
## Features

* **Minimal Dependencies**:
This script depends only on 2 custom functions and no plugins.

* **Specify a Custom Delimiter Character**:
By default we use the comma character but you can pass a custom delimiter.

* **Ignore Empty Columns**:
You can specify a setting that allows the JSON to ignore empty columns.

<!-- GETTING STARTED -->
## Getting Started

### Prerequisites

#### Version

The FileMaker script makes use of the [JSON Functions](https://fmhelp.filemaker.com/help/16/fmp/en/index.html#page/FMP_Help/json-functions.html) introduced in FileMaker 16.

This means that this script will only work with **FileMaker 16+** products.

Using the script with anything less than 16 will have unexpected behaviour.

#### Custom Functions

We make use of the #Name-Value custom function provided by [filemakerstandards](https://github.com/filemakerstandards/fmpstandards/tree/master/Functions/%23Name-Value).

Please copy the following Custom Functions to your solution before copying the script:
- [# ( name ; value )](https://raw.githubusercontent.com/filemakerstandards/fmpstandards/master/Functions/%23Name-Value/%23.fmfn)
- [#Assign ( parameters )](https://raw.githubusercontent.com/filemakerstandards/fmpstandards/master/Functions/%23Name-Value/%23Assign.fmfn)

#### Limitations

##### Large CSV Data

FileMaker Pro is not the most efficient tool for text parsing. This script was designed primarily for small CSV data. It wasn't designed, in mind, to convert large CSV files into JSON.

However, if given enough time, this script will convert large CSV files into JSON and has been optimised to the best of our ability.

Unfortunately, FileMaker can only go so far before it starts to fall over.

If you do have this need, we **strongly** suggest using a plugin or performing the conversion outside of FileMaker and then importing the result back into FileMaker.

##### FileMaker Text Parsing Functions

We have built the rules for identifying CSV columns in FileMaker using all the Text Functions available to us and from our testing it has handled all the testing CSV data thrown at it.

However, there may be some fringe cases where this breaks down. If you discover such a case, please create a [Bug Report](https://github.com/stevenwhitespacesystems/fm-csv2json/issues) and we'll see if we can correct it. Unfortunately, there may be cases that can't be solved.

<!-- USAGE EXAMPLES -->
## Usage

### Installation

1. Make sure that the [Custom Functions](#custom-functions) have been added to your solution.
2. Copy the `fm-csv2json` script to your solution.

### Quick Start

There are 2 fmp12 files provided here

1. fm-csv2json.fmp12
2. fm-csv2json-tests.fmp12

`fm-csv2json.fmp12` file contains the script and custom function that you need to copy over.
  
`fm-csv2json-tests.fmp12` file contains our test suite to confirm that the script behaves as intended.

If you open the `fm-csv2json` file, you can paste in some xml and convert it to a json object by pressing the Convert button.

### Required Parameters

The below parameters can be used as `# ( name ; value )` parameters for the script and must be passed:

| `name`              | Type            | Description |
|:--------------------|:----------------|:------------|
| `csv`               | `text`          | The CSV String you want to turn into a JSON |
| `json_field_name`   | `text`          | Fully Quanlified field name for storing the result.

#### Optional Parameters

The below parameters can be used and are optional:

| `name`              | Type            | Default `value` | Description |
|:--------------------|:----------------|:---------------|:------------|
| `header`            | `bool`          | `false`        | Tells the parser that the first row is headers, and should be used as a JSON key. | 
| `use_type`          | `bool`          | `false`        | Will make the parser try to determine the correct JSON type. e.g. "15.00" will be used in JSON as 15. |
| `quote`             | `text`          | `"`            | The character being used to group columns between delimiters. |
| `delimiter`         | `text`          | `,`            | The charater being used to distinguish columns. |
| `trim`              | `bool`          | `false`        | Will trim any leading or trailing whitespace from header and values. |
| `ignore_empty`      | `bool`          | `false`        | Will ignore any columns that don't have data in them. |

<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to be learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE` for more information.

<!-- CONTACT -->
## Contact

Steven McGill - [WhiteSpace Systems Ltd](https://whitespacesystems.co.uk) - [steven@whitespacesystems.co.uk](mailto:steven@whitespacesystems.co.uk)

Project Link: [fm-csv2json](https://github.com/stevenwhitespacesystems/fm-csv2json)

<!-- ACKNOWLEDGEMENTS -->
## Acknowledgements
* [Jeremy Bante's #Parameters](http://www.modularfilemaker.org/module/parameters/)
* [csvtojson](https://github.com/Keyang/node-csvtojson)
* [Computech IT Services](https://www.computech-it.co.uk)
* [Best-README-Template](https://github.com/othneildrew/Best-README-Template)

<!-- FMAPI SUITE -->
## fmapi Product Suite

When FileMaker 16 introduced cURL with the Insert from URL script step. Use cases for FileMaker Pro increased dramatically in relation to REST APIs.

It allowed developers to finally communicate with other web services and APIs without the need for 3rd party plugins. Integration with Couriers, Payment Gateways & Social Media Sites all became within touching distance.

However, without prior knowledge of cURL, HTTP Request Methods, HTTP Headers, JSON, OAuth Authentication, API Keys, API documentation etc, it can be extremely difficult to get started for the novice user or even the most proficient FileMaker developer.

And with that comes our goal, to simplify communications between your FileMaker App and the vast amount of Web Services available, no matter your ability level.

Read more over at [What is fmapi?](https://whitespacesystems.co.uk/filemaker-3rd-party-api-integration/)

### fmapi Apps

A collection of FileMaker apps that communicate directly with popular 3rd party REST APIs.

* [fmapi-vies-vat](https://whitespacesystems.co.uk/portfolio-item/filemaker-vies-vat-integration/) - Integrate the EU Commissions Vies VAT API directly into you FileMaker App allowing you to validate EU VAT Numbers.

<!-- MARKDOWN LINKS & IMAGES -->
[filemaker-shield]: https://img.shields.io/badge/filemaker-%3E%3D%2016.0.0-009edb.svg
[platform-shield]: https://img.shields.io/badge/platform-Pro%20%7C%20Go%20%7C%20Server%20%7C%20Webdirect%20%7C%20Cloud-purple.svg
[contributors-shield]: https://img.shields.io/github/contributors/stevenwhitespacesystems/fm-csv2json.svg
[license-shield]: https://img.shields.io/badge/license-MIT-blue.svg
[commit-shield]: https://img.shields.io/github/last-commit/stevenwhitespacesystems/fm-csv2json.svg
[license-url]: https://choosealicense.com/licenses/mit
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?logo=linkedin&colorB=0077B5
[linkedin-url]: https://www.linkedin.com/company/whitespace-systems-ltd/
[facebook-shield]: https://img.shields.io/badge/-facebook-white.svg?logo=facebook&colorB=3578E5
[facebook-url]: https://www.facebook.com/WhitespaceSystemsLtd/