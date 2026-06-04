# Partie 1 : Exploration des Transformers et Tâches NLP

## 1. Introduction à HuggingFace Transformers

HuggingFace Transformers est une bibliothèque open-source qui fournit des milliers 
de modèles pré-entraînés pour le traitement du langage naturel (NLP). Elle permet 
de charger facilement des modèles, d'utiliser des tokenizers et de créer des 
pipelines simplifiés pour diverses tâches NLP.

## 2. Tokenizers

Un tokenizer convertit le texte brut en tokens (unités) compréhensibles par le modèle.

**Exemple avec BERT :**
- Texte : "Artificial intelligence is transforming the world."
- Tokens : ['artificial', 'intelligence', 'is', 'transforming', 'the', 'world', '.']
- IDs    : [101, 7976, 4454, 2003, 17903, 1996, 2088, 1012, 102]
- [CLS] et [SEP] sont des tokens spéciaux ajoutés automatiquement par BERT.

## 3. Tâches NLP Implémentées

### 3.1 Classification de Texte
**Modèle :** distilbert-base-uncased-finetuned-sst-2-english  
**Résultats :**
- "I love this movie!" → POSITIVE (0.9998)
- "This product is terrible." → NEGATIVE (0.9997)
- "The weather is okay today." → POSITIVE (0.9997)

### 3.2 Analyse de Sentiment
**Modèle :** nlptown/bert-base-multilingual-uncased-sentiment  
**Résultats :**
- "J'adore ce produit, il est fantastique!" → 5 stars (0.848)
- "C'est vraiment décevant, je suis déçue." → 2 stars (0.517)
- "Le service est correct, rien d'exceptionnel." → 3 stars (0.663)

### 3.3 Question Answering
**Modèle :** deepset/minilm-uncased-squad2  
**Résultats :**
- Q: "What is artificial intelligence?" → A: "a field of computer science"
- Q: "In which fields is AI used?" → A: "medicine, finance and education"

### 3.4 Résumé Automatique
**Modèle :** sshleifer/distilbart-cnn-12-6  
**Résultat :**
"AI is being used today across different industries including healthcare, finance 
and education. Machine learning allows computers to learn from data without being 
explicitly programmed."

## 4. État de l'Art : Systèmes RAG

### 4.1 Définition
RAG (Retrieval-Augmented Generation) est une architecture qui combine deux composants :
- **Retrieval** : récupération de documents pertinents depuis une base de connaissances
- **Generation** : génération de réponse par un LLM basée sur ces documents

### 4.2 Limites des LLMs sans RAG
- Connaissances figées à la date d'entraînement
- Hallucinations : génèrent des informations fausses
- Pas d'accès aux données privées ou internes
- Coût élevé du re-entraînement pour mise à jour

### 4.3 Comparaison des Approches

| Approche | Avantages | Inconvénients |
|----------|-----------|---------------|
| Fine-tuning | Très précis sur domaine spécifique | Coûteux, données nécessaires |
| Prompt Engineering | Rapide, sans entraînement | Limité par la fenêtre de contexte |
| RAG | Dynamique, précis, économique | Pipeline plus complexe |

### 4.4 Variantes Modernes de RAG
- **Naive RAG** : pipeline simple retrieve → generate
- **Advanced RAG** : re-ranking, query expansion, hybrid search
- **Modular RAG** : composants interchangeables selon le besoin
- **GraphRAG** : utilise des graphes de connaissances pour mieux structurer l'information