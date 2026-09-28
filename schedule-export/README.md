# Schedule Batch Export to CSV

Export every schedule in a Revit model to CSV in one click. Each schedule becomes its own file, named after the schedule, ready to open in Excel or feed into a cost or quantity workflow.

## The problem

Revit only exports schedules one at a time, and each export asks for the same options again. On projects with dozens of quantity schedules, that means repetitive clicks every time the model changes. There is also a regional issue: in countries where Excel uses a comma as the decimal separator (most of Latin America and Europe), comma-delimited CSV files open in a single column.

## How it works

1. Collects all schedules in the active model.
2. Skips titleblock revision schedules.
3. Cleans characters that are not valid in file names.
4. Exports each schedule as `<schedule name>.csv` to the chosen folder, with:
   - the delimiter you choose (`;` by default),
   - one header row,
   - text wrapped in double quotes,
   - no title row and no blank or group header rows, so the data is clean for analysis.
5. Returns the list of exported schedules.

## Requirements

- Revit with Dynamo 3.3 or later (built with Dynamo 3.3.0)
- No external packages required (uses a Python Script node with the Revit API)

## Usage

1. Open `schedule-export.dyn` in Dynamo.
2. In the **Directory Path** node, browse to the folder where the CSV files will be saved. The folder must already exist.
3. In the **String** node, set the delimiter:
   - `;` for Excel in Spanish, Portuguese, French, German and other comma-decimal regions (default)
   - `,` for Excel in English (US/UK)
4. Run. The output shows the names of the exported schedules.

## Known limitations

- Exports **all** schedules in the model; there is no filter by name yet.
- Existing files with the same name in the folder are overwritten.
- If one schedule fails to export, the run stops at that schedule.

---

## Español

Exporta todas las tablas de planificación de un modelo de Revit a CSV en un solo paso, un archivo por tabla con su nombre. Permite elegir el delimitador: `;` para Excel en español (valor por defecto) o `,` para Excel en inglés. Exporta datos limpios, sin fila de título ni filas en blanco, listos para Excel o para flujos de cuantificación.

## Author

**Fernando Batz** — Architect & BIM Specialist
[LinkedIn](https://www.linkedin.com/in/fernando-batz-bim)

## License

MIT
