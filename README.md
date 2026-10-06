# Welcome

<img width="600" height="562" alt="image" src="https://github.com/user-attachments/assets/62f5674b-d25d-4ab0-8617-a380901b0279" />

## Purpose

I kept writing the same prompts and projects over and over, so I wanted to generate a baseline set of files to use in Claude (or others) for work.

## Usage

1. For those who don't live on git, download the *.zip file from the repo.

<img width="1892" height="918" alt="image" src="https://github.com/user-attachments/assets/9a2d74f6-1336-415b-9661-a0d0911dad4f" />

2. Start a project in Claude.

2.b When starting the project, include the zip file in the optional context area.

<img width="1056" height="918" alt="image" src="https://github.com/user-attachments/assets/ba177654-6dfd-45e0-a7eb-e095fd9da8f5" />

3. Once the project starts, issue a prompt like this:

```
The included zip file contains the project file structure. We will make edits once unpacked. Unpack now.
```

Once complete, the file structure will almost be in place; now issue these commands:

```
Let's edit the files:

Delete the claude-generic... folder, but first move all of the internal data in the dir to the same level as Artifacts
```

Finally, review the `extras` folder, move any files wanted into the `.claude` folder, then run this command:

```
Delete the ' extras' directory and all contents

Delete git artifacts and the original zip file.
```


**Done, for now**
