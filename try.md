flowchart TD
    %% Stage 1: Data Acquisition & Preprocessing
    A1(["📡 IMU Sensor Data Acquisition"])
    A2(["🧹 Outlier Removal (Z-score Filter)"])
    A3(["🔗 Sequence Generation (64-sample Windows)"])
    A4(["🧮 Feature Extraction (13 Time-domain Stats)"])
    A5(["⚖️ Data Normalization (Zero Mean, Unit Variance)"])
    A6(["🔀 Train-Test Split (80/20 Stratified)"])

    %% Stage 2: Model Pipeline
    B1(["🔄 BiLSTM Layer 1 (64 Units, Bidirectional)"])
    B2(["🧊 BatchNorm + Dropout (0.2)"])
    B3(["🔄 BiLSTM Layer 2 (32 Units, Bidirectional)"])
    B4(["📏 Global Max Pooling"])
    B5(["🔗 Dense Output Layer (20 Classes)"])

    %% Stage 3: Evaluation & Output
    C1(["📊 Multiclass Confusion Matrix"])
    C2(["📈 Metrics: Accuracy, Precision, Recall, F1"])
    C3(["⏱️ Real-Time Quality Metrics: QAC, QACT"])
    C4(["🚦 Fault Diagnosis Output"])

    %% Stage 4: Feedback Loop
    D1(["🔄 Model Update / Retrain (if new data or faults)"])

    %% Connections
    A1 --> A2
    A2 --> A3
    A3 --> A4
    A4 --> A5
    A5 --> A6
    A6 --> B1
    B1 --> B2
    B2 --> B3
    B3 --> B4
    B4 --> B5
    B5 --> C1
    C1 --> C2
    C2 --> C3
    C3 --> C4
    C4 --|Performance Monitoring| D1
    D1 --|New Data| A1

    %% Styling for clarity
    classDef input fill:#e3f2fd,stroke:#2196f3,stroke-width:2px;
    classDef model fill:#e8f5e9,stroke:#43a047,stroke-width:2px;
    classDef output fill:#fff3e0,stroke:#fb8c00,stroke-width:2px;
    classDef feedback fill:#fce4ec,stroke:#d81b60,stroke-width:2px;
    class A1,A2,A3,A4,A5,A6 input;
    class B1,B2,B3,B4,B5 model;
    class C1,C2,C3,C4 output;
    class D1 feedback;
