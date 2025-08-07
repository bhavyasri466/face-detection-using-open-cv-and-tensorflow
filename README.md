# face-detection-using-open-cv-and-tensorflow
# Wrong Tag Frame Facial Processor

This project processes wrongly tagged race event frames from a MongoDB database and verifies participant identities using facial recognition. It compares faces in the images with pre-registered participant faces using stored facial embeddings.

## 🔧 Requirements

- Python 3.8+
- MongoDB with GridFS
- FaceNet-compatible pickled encodings
- Registered participant images encoded as `.pickle` files

### 📦 Python Dependencies

Install dependencies using:

```bash
pip install -r requirements.txt
```

**requirements.txt**:

```
opencv-python
face_recognition
pillow
numpy
pandas
pymongo
```
You can generate this file using:
```bash
pip freeze > requirements.txt
```

## ⚙️ Configuration

Create a `mongodb_config.properties` file in the root directory:

```ini
mongo_uri=mongodb://localhost:27017/
database_name=your_db_name
petdate=07-08-2025
encoding_threshold=0.6
```

## 📁 Project Structure

```
project/
├── everybatchpicklefiles0307/       # Folder containing registration .pickle files
├── mongodb_config.properties         # MongoDB & config settings
├── facial_processor.py               # Main processing script
├── facial_logs_<timestamp>.xlsx      # Output logs (auto-generated)
├── requirements.txt
```

## 🚀 Running the Project (in Visual Studio Code)

1. Open project folder in VS Code.
2. Create a virtual environment and activate it:
    ```bash
    python -m venv venv
    source venv/bin/activate  # or venv\Scripts\activate on Windows
    pip install -r requirements.txt
    ```
3. Open `facial_processor.py`.
4. Click **Run > Run Without Debugging**, or:
    ```bash
    python facial_processor.py
    ```

## 🧠 What It Does

- Loads registered participant facial embeddings from `.pickle` files.
- Fetches wrongly tagged frames from MongoDB.
- Downloads and decodes images from GridFS.
- Uses `face_recognition` to detect and match faces.
- Inserts matched info into `bib_detection_results`.
- Saves log as an Excel sheet.

## 📤 Output

- Updated MongoDB flags
- Insertions into `bib_detection_results`
- Excel logs: `facial_logs_<timestamp>.xlsx`

## 🧪 Testing Tips

- Ensure MongoDB is populated and accessible.
- Validate `.pickle` file format before running.
- Tune `encoding_threshold` in config if too strict or lenient.

## 🧹 Cleanup

```bash
deactivate
```

---

Built with ❤️ using Python, OpenCV, and MongoDB.
