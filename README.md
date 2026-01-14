# **Melody Similarity Retrieval**

This project explores methods for **melodic similarity retrieval** using symbolic music (MIDI). It includes a full preprocessing pipeline, classical and neural retrieval baselines, and trained models for embedding melodies into a vector space.

Two main model families are provided:

* **Autoencoder-based embeddings**
* **Contrastive learning–based embeddings**

Evaluation includes traditional edit-distance baselines (Levenshtein), neural embeddings, and qualitative visualization tools.

---

## **Features**

* Melody extraction from multi-track MIDI
* Key normalization and interval-based representation
* Snippet construction with overlapping windows
* Autoencoder architecture for unsupervised embedding learning
* Contrastive encoder with InfoNCE loss and time-based positive sampling
* Baseline retrieval using Levenshtein distance
* Precision@K evaluation
* Demo scripts and example snippets

---

## **Repository Structure**

```
data/
    ├── demo/                        # Example queries and retrieved snippets
        ├── snippet_midis/
            ├── query/               # Query snippets used for demo retrieval
            └── retrieved/           # Example retrieved library snippets
        ├── ABBA.Mamma Mia K.mid     # Example MIDI files
        ├── MAROON 5.She will be loved K.MID
        └── snippet_201_song4.mid    # Example snippet
    ├── lastfm/                      # (Optional) Metadata or tags for songs
    ├── processed/
        └── snippets.npz             # Preprocessed snippet dataset (intervals, durations, metadata)
    ├── raw_midi/                    # Raw unprocessed MIDI files
    └── md5_to_paths.json            # Mapping from MIDI hashes → file paths

models/
    ├── autoencoder.pt               # Trained autoencoder checkpoint
    └── contrastive_encoder.pt       # Trained contrastive encoder checkpoint

notebooks/                           # All development and analysis notebooks
    ├── autoencoder_embeddings.ipynb
    ├── baseline_retrieval.ipynb
    ├── contrastive_autoencoder_model.ipynb
    ├── dataset_creation.ipynb
    ├── debug.ipynb
    ├── demo.ipynb
    ├── evaluate_melody_similarity.ipynb
    ├── preprocess_midi.ipynb
    └── search_in_json.ipynb

.gitignore
README.md
requirements.txt                     # Python dependencies
```

---

## **Getting Started**

### **1. Install dependencies**

```bash
pip install -r requirements.txt
```

### **2. Prepare data**

Place raw MIDI files into:

```
data/raw_midi/
```

Run the preprocessing notebook:

```
notebooks/preprocess_midi.ipynb
```

This generates `snippets.npz` and related metadata.

### **3. Train models**

Autoencoder:

```
notebooks/contrastive_autoencoder_model.ipynb
```

Contrastive encoder:

```
notebooks/contrastive_autoencoder_model.ipynb
```

(Contains both architectures.)

### **4. Run retrieval demo**

Use:

```
notebooks/demo.ipynb
```

This performs retrieval using:

* Levenshtein baseline
* Autoencoder embeddings
* Contrastive embeddings

### **5. Evaluate**

Open:

```
notebooks/evaluate_melody_similarity.ipynb
```

Metrics include Precision@K and qualitative embedding visualizations.

---

## **Demo Files**

The `data/demo/` directory contains:

* Query snippets
* Retrieved snippets
* Example MIDI files

You can load and listen to these to understand how the model behaves.


