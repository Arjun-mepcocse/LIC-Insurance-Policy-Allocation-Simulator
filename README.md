<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=4C1D95&height=200&section=header&text=LIC%20Policy%20Allocation%20Simulator&fontSize=36&fontColor=ffffff&animation=fadeIn&fontAlignY=38" width="100%" alt="LIC Policy Allocation Simulator banner" />

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&pause=1000&color=A78BFA&center=true&vCenter=true&width=600&lines=Java+Console+Application;LIC+Plan+Recommendation+Engine;Clean+Input+Handling+%26+Logic" alt="Typing animation" />

<br/>

<img src="https://img.shields.io/badge/Java-8%2B-4C1D95?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java" />
<img src="https://img.shields.io/badge/Type-Console%20App-6D28D9?style=for-the-badge" alt="Console App" />
<img src="https://img.shields.io/badge/License-MIT-8B5CF6?style=for-the-badge" alt="License" />

</div>

# LIC Policy Recommender (Console App)

A small, beginner-friendly Java command-line program that collects a few personal details about a prospective policyholder and suggests a matching LIC (Life Insurance Corporation of India) plan based on age and need.

I built this as a practice project to get comfortable with user input handling, conditional logic, and clean console interaction in Java. It's intentionally simple, easy to read, and easy to extend.

---

## Table of Contents

- [Features](#features)
- [How It Works](#how-it-works)
- [Getting Started](#getting-started)
- [Sample Run](#sample-run)
- [Project Structure](#project-structure)
- [Known Issues](#known-issues)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [License](#license)

---

## Features

- Interactive prompts that walk the user through a short questionnaire
- Captures personal and family details: name, gender, age, marital status, parents' names, and sibling information
- Recommends an LIC plan based on the person's age (and, for young adults, their stated insurance need)
- Zero dependencies: just the Java standard library

## How It Works

The program reads input from the console using `Scanner` and collects the following:

| Field | Type | Example |
|-------|------|---------|
| Policymaker name | `String` | `XYZ` |
| Alive status (Y/N) | `String` | `Y` |
| Gender (M/F) | `String` | `M` |
| Age | `double` | `27` |
| Marital status | `String` | `Single` |
| Father's name | `String` | `ABC` |
| Mother's name | `String` | `DEF` |
| Number of siblings | `int` | `5` |
| Sibling's name | `String` | `GHI` |
| Sibling's age | `double` | `24` |

Based on the age, the program suggests one of the following plans:

- **New Children's Money Back Plan**
- **Digi Term** (when the stated status is `Protection`)
- **LIC Yuva Term** (for any other status)

## Getting Started

### Prerequisites

- Java Development Kit (JDK) 8 or later

Check your installation:

```bash
java -version
javac -version
```

### Installation and Running

1. Clone the repository:

   ```bash
   git clone https://github.com/<your-username>/<your-repo-name>.git
   cd <your-repo-name>
   ```

2. Compile the program:

   ```bash
   javac Lic.java
   ```

3. Run it:

   ```bash
   java Lic
   ```

## Sample Run

```text
Enter name of the policymaker:
XYZ

Enter whether the person is alive or not? (Y/N):
Y

Enter the gender of the person (M/F):
M

The age of the person is:
27

Enter the marital status of the person:
Single

Enter the father's name of the person:
ABC

Enter the mother's name of the person:
DEF

Enter the number of siblings:
5

The number of siblings to the person is 5

Enter the name of the sibling:
GHI

Enter the sibling's age:
24

New Children's Money Back Plan
```

## Project Structure

```text
.
├── Lic.java    # Main program: input collection and plan recommendation
└── README.md   # You are here
```

## Known Issues

I believe in being upfront about the rough edges, so here's what's currently on my list to fix:

- **Plan logic overlap:** the first condition (`age > 18`) matches every adult, which means the second branch (ages 18 to 25, with the Digi Term / LIC Yuva Term choice) is never reached. As a result, the sample run above (age 27) suggests the Children's Money Back Plan, which isn't the intended outcome. The age ranges need to be reordered or tightened.
- **No input validation:** entering text where a number is expected (for example, a letter for age) will crash the program with an `InputMismatchException`.
- **Single sibling only:** the program asks for the number of siblings but only records one sibling's name and age.
- **No output for some ages:** users aged 18 or under fall through without any plan being suggested.

## Roadmap

- [ ] Fix the age-range logic so each age group gets the right plan
- [ ] Add input validation and friendly error messages
- [ ] Loop through all siblings instead of just one
- [ ] Add a fallback recommendation for minors
- [ ] Refactor into separate methods or classes (e.g., `Policyholder`, `PlanRecommender`)
- [ ] Add unit tests
- [ ] Store results to a file or database

## Contributing

Suggestions and pull requests are always welcome, especially from fellow learners. If you'd like to contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/your-idea`)
3. Commit your changes (`git commit -m "Add your idea"`)
4. Push to the branch (`git push origin feature/your-idea`)
5. Open a pull request

For bigger changes, please open an issue first so we can talk it through.

## License

This project is released under the [MIT License](LICENSE). Feel free to use it, learn from it, and build on it.

## Disclaimer

This is an educational project. It is not affiliated with or endorsed by the Life Insurance Corporation of India, and its output should not be treated as financial or insurance advice. Please consult an authorized LIC agent or the official LIC website before choosing a policy.

---

Built with curiosity and a lot of `Scanner` calls. If this helped you, a star is much appreciated.
