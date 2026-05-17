# Image Metadata & Geolocation Lab

## Objective

Extract metadata from an image file and identify the true location of the photo despite tampered or invalid GPS coordinates.

---

## Tools Used

- **ExifTool** — command-line metadata extraction tool
- **Google Reverse Image Search** — used to identify the photo's actual location

---

## Steps

### 1. Extract Metadata with ExifTool

Ran ExifTool against the target image to extract embedded EXIF metadata:

```bash
exiftool image.jpg
```

Key fields extracted:

| Field | Value |
|---|---|
| GPS Latitude | 32 deg 40' 3.87" S |
| GPS Longitude | 279 deg 29' 31.87" W |
| File Type | JPEG |

### 2. Analyse the GPS Coordinates

The extracted GPS longitude value of **279° W** is outside the valid range for standard GPS coordinates (0°–180°). This indicated the coordinates had been **tampered with or were incorrectly recorded**.

Attempting to convert using the 0–360° bearing system:

```
360° - 279° = 81° E
```

This placed the coordinate in the **Southern Indian Ocean** — an uninhabited stretch of open water — which was inconsistent with the image content.

**Conclusion:** The embedded GPS data was unreliable and could not be used directly to determine the photo's location.

### 3. Reverse Image Search

Since the GPS coordinates were invalid, a **Google Reverse Image Search** was performed by uploading the image to [images.google.com](https://images.google.com).

The search returned matching or visually similar results that identified the true location of the photo.

**Identified Location:** *Kathmandu*

---

## Findings

| Method | Result |
|---|---|
| ExifTool GPS | Invalid — 279° W is out of range |
| Coordinate conversion | Southern Indian Ocean (open water) — inconsistent with image |
| Reverse Image Search | Successfully identified true location |

---

## Conclusion

The GPS coordinates embedded in the image's EXIF metadata were tampered with or incorrectly set, making them useless for direct geolocation. By combining metadata analysis with open-source intelligence (OSINT) techniques — specifically Google Reverse Image Search — the actual location of the photograph was successfully identified.

This demonstrates the importance of **not relying solely on embedded metadata** when geolocating an image, and the value of cross-referencing with OSINT tools.

---

*Lab completed using ExifTool and Google Reverse Image Search.*
