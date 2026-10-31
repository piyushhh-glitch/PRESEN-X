# PRESEN-X

PRESEN-X is a Streamlit attendance application for teachers and students. It stores its data in Supabase and supports taking attendance from classroom photos or recorded voice input.

## Features

### Teacher workflow

- Register and sign in with a username and password.
- Create subjects with a subject code, name, and section.
- Share a subject code or QR-backed join link with students.
- Capture or upload classroom photos, run face analysis, review the result, and save attendance.
- Record classroom audio for voice attendance, review the result, and save attendance.
- View attendance records grouped by timestamp, subject, and subject code.

### Student workflow

- Sign in with a camera-based face check.
- Register a new profile with a face embedding; a voice recording is optional.
- Enroll in a subject with its code or through a `join-code` link.
- View enrolled subjects, attendance totals, and attended-class totals.
- Unenroll from a subject.

## How attendance works

- **Face attendance:** dlib generates face embeddings; a linear SVC is trained from stored student embeddings.
- **Voice attendance:** Resemblyzer creates voice embeddings from recorded audio and compares them with enrolled students who have voice samples.
- Teachers review the generated result and select **Confirm & Save** before attendance records are written.

## Technology

- Streamlit
- Supabase
- dlib, `face_recognition_models`, and scikit-learn
- Resemblyzer and librosa
- pandas, NumPy, Pillow, bcrypt, and segno

## Project structure

```text
app.py                         # Streamlit entry point and route selection
database/schema.sql             # Supabase table schema
requirements.txt                # Python dependencies
.streamlit/config.toml          # Streamlit server and theme settings
src/
  components/                   # Dialogs, headers, footers, and subject cards
  database/                     # Supabase client and data-access helpers
  pipelines/                    # Face and voice recognition pipelines
  screens/                      # Home, teacher, and student screens
  ui/                           # Layout and styling helpers
```
