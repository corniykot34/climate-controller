# References

Store downloaded manufacturer datasheets, mechanical drawings, and other stable primary references here.

Recommended structure:

```
references/
└── datasheets/
    ├── ESP32-WROOM-32E_*.pdf
    ├── SHT31_*.pdf
    ├── PEC11R_*.pdf
    └── ...
```

Do not add a PDF merely because it was found through search. Prefer the component manufacturer or official vendor source, and record the exact part number/revision in `docs/BOM.md`.

Binary reference files can be added later from the local project workspace.
