# HostelHive Documents

Project documentation for **HostelHive**, a QR-based hostel management system
built for the SENG 34213 System Development Project (Software Engineering
Teaching Unit, University of Kelaniya).

This repository is the `documents/` folder referred to in the project
guideline (Chapter 10.1, Final Deliverables). Each deliverable is stored at the
path the guideline specifies.

## Team

| Name               | Student No. |
| ------------------ | ----------- |
| Hasinthaka Piyumal | SE/2021/036 |
| Navon Sanjuni      | SE/2021/061 |
| Thagya Kavindi     | SE/2021/062 |
| Tasheen Darshika   | SE/2021/030 |

## Deliverables

| #  | Artefact                       | Location                                | Status      |
| -- | ------------------------------ | --------------------------------------- | ----------- |
| 1  | Updated SRS                    | `srs/srs-final.pdf`                     | Pending     |
| 2  | Updated SDS                    | `sds/sds-final.pdf`                     | Pending     |
| 6  | Test Coverage Report           | `testing/coverage-sprint8.pdf`          | Pending     |
| 7  | Test Case Register             | `testing/test-register.pdf`             | Pending     |
| 8  | OWASP Compliance Evidence      | [`security/owasp-checklist.pdf`](security/owasp-checklist.pdf) | Version 1.0 |
| 9  | Performance Test Results       | `testing/performance-report.pdf`        | Pending     |
| 11 | Retrospective Reports          | `retrospectives/`                       | Pending     |

The source code, CI/CD pipelines and deployed application URL live in the
code repositories of the [Hostel-Hive](https://github.com/Hostel-Hive)
organisation:

- [hostelhive-backend](https://github.com/Hostel-Hive/hostelhive-backend): Go API, migrations, backend tests
- [hostelhive-frontend](https://github.com/Hostel-Hive/hostelhive-frontend): React web dashboard
- [hostelhive-mobileapp](https://github.com/Hostel-Hive/hostelhive-mobileapp): Flutter mobile app
- [hostelhive-hardware](https://github.com/Hostel-Hive/hostelhive-hardware): ESP32 QR scanner firmware
- [hostelhive-infra](https://github.com/Hostel-Hive/hostelhive-infra): Docker Compose, Nginx, deployment

## Repository layout

```
documents/
├── README.md
├── .gitignore
└── security/
    ├── owasp-checklist.pdf        # Deliverable 8 (built PDF, committed)
    └── src/
        ├── owasp-checklist.tex    # LaTeX source
        └── figures/               # Screenshots used in the PDF
```

## Building the LaTeX documents

The documents are written in LaTeX and follow the formatting of the HostelHive
SRS (Times New Roman 12 pt, 1.5 line spacing, centred chapter headings).

### Option 1: Tectonic (recommended, downloads packages automatically)

```bash
cd security/src
tectonic -X compile owasp-checklist.tex --outdir ..
```

### Option 2: TeX Live / MiKTeX

```bash
cd security/src
pdflatex -output-directory=.. owasp-checklist.tex
pdflatex -output-directory=.. owasp-checklist.tex
```

Run `pdflatex` twice so the table of contents and the lists of tables are
filled in. Build artefacts (`*.aux`, `*.log`, `*.toc`, ...) are ignored by
`.gitignore`.

### Screenshots

All screenshots used in the OWASP document are in `security/src/figures/`.
The build stops with an error if one of them is missing, so the PDF never
has an empty spot.

| File name              | What it shows                                        |
| ---------------------- | ---------------------------------------------------- |
| `ci-backend.png`       | Latest Backend CI run on GitHub Actions              |
| `ci-frontend.png`      | Latest Frontend CI run, including the npm audit job  |
| `ci-mobile.png`        | Latest mobile app CI run                             |
| `ci-hardware.png`      | Latest ESP32 firmware CI run                         |
| `auth-tests.png`       | Backend login and role check tests passing          |
| `input-tests.png`      | Backend input checking tests passing                 |
| `error-responses.png`  | Real 401, 403 and 503 responses from the backend     |
| `dependency-check.png` | `go mod verify` and `npm audit` results              |
| `govulncheck.png`      | govulncheck on the backend before the Go upgrade     |
| `govulncheck-after.png`| govulncheck on the backend after the Go upgrade      |
| `api-https.png`        | HTTPS, redirect and TLS version checks on the API (Render) |
| `web-https.png`        | HTTPS redirect and HSTS on the web dashboard (Vercel) |
| `request-log.png`      | Backend log lines for refused, allowed and failed requests |

To update a screenshot, replace the file with the same name and rebuild.

## Updating a document

1. Edit the `.tex` source.
2. Add a row to the document's Version History table.
3. Rebuild the PDF and commit both the `.tex` and the `.pdf`.
