# Upload this lab to GitHub

This folder is prepared for a new repository. The completion flag is stored in `private/flag.txt`, and `private/` is ignored by Git. For extra safety, stage only the files listed below rather than using `git add .`.

## 1. Create an empty GitHub repository

On GitHub, create a new repository, for example `icmp-ping-thm-lab`. Do not initialize it with a README, license, or `.gitignore`, because those files are already in this folder.

## 2. Open a terminal in this folder

Run:

```bash
git init
git branch -M main
```

## 3. Stage only the public project files

```bash
git add README.md REPORT.md GITHUB_UPLOAD.md .gitignore evidence/README.md logs/ping-output.txt
git status --short
```

Check that `private/flag.txt` is **not** listed as a staged file.

## 4. Commit the project

```bash
git commit -m "Add ICMP ping lab documentation"
```

## 5. Connect your repository and push

Replace the placeholder with the URL of the empty repository you created:

```bash
git remote add origin https://github.com/YOUR-USERNAME/icmp-ping-thm-lab.git
git push -u origin main
```

## 6. Add your screenshots

Copy your own sanitized screenshots into `evidence/`, using the filenames in `evidence/README.md`. Then stage and push them:

```bash
git add evidence/*.png
git commit -m "Add ICMP lab evidence screenshots"
git push
```

Only add screenshots you actually captured. Do not commit raw packet captures unless you have reviewed them for private traffic and identifiers.
