# Parking Numbering by Path

Automatically number parking spaces in Revit following a path line you draw. Instead of typing numbers one by one, you sketch the route through the parking lot and Dynamo numbers every space in that order.

## The problem

Numbering hundreds of parking spaces in a basement is slow and error-prone. Numbering them in a logical sequence (following the driving route or the ramps) is even harder when spaces were placed in a different order during modeling.

## How it works

1. Draw a **model line** that passes through every parking space, in the order you want them numbered.
2. The script divides the line into evenly spaced points.
3. For each point, it detects which Parking element contains it (using the element's bounding box).
4. Duplicates are removed while keeping the order along the path.
5. Spaces are numbered sequentially (1, 2, 3…) in the chosen parameter.

## Requirements

- Revit with Dynamo 3.2 or later (built with Dynamo 3.2.1)
- No external packages required
- Parking spaces modeled with the **Parking** category
- A text parameter to store the number. The script uses `Marca` (Mark) by default.

> **Recommended:** create a shared text parameter named `No. Aparcamiento` for the Parking category. `Mark` is often already used for other purposes, while a dedicated parameter keeps the numbering clean and can be used in schedules and tags.

## Usage

1. (Optional, recommended) Create the shared parameter `No. Aparcamiento`.
2. Draw the path model line (see tips below).
3. Open `parking-numbering.dyn` in Dynamo.
4. In the **Select Model Element** node, select your path line.
5. The **Code Block** contains `"Marca"`. If you created your own parameter, replace it with its exact name, e.g. `"No. Aparcamiento"`. In English Revit, use `"Mark"`.
6. Adjust the **Integer Slider** if needed (number of sample points along the line; default 400).
7. Run.

## Tips for drawing the path line

The numbering order depends on the line, so how you draw it matters:

- Draw the line **at the same height as the parking spaces**, so it actually touches them.
- Pass through the **center** of each space, not along its edges or corners.
- Avoid crossing neighboring spaces you don't want numbered yet.
- For long paths, increase the slider so no small space is skipped.

## Known limitations

- Bounding boxes are aligned to the project axes and may be larger than the space itself (if the family includes a car, wheel stops, etc.). When two boxes overlap, the order of those two spaces may not follow the line. Review the result and correct manually if needed.
- Existing values in the parameter are overwritten.

---

## Español

Numera automáticamente los parqueos en Revit siguiendo una línea de recorrido. Se dibuja una línea de modelo que toca los parqueos en el orden deseado, se selecciona en Dynamo y el script asigna la numeración consecutiva en el parámetro Marca. Se recomienda crear un parámetro compartido "No. Aparcamiento" y escribir su nombre en el Code Block del script.

## Author

**Fernando Batz** — Architect & BIM Specialist
[LinkedIn](https://www.linkedin.com/in/fernando-batz-bim)

## License

MIT
