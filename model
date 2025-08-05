######model#####
import numpy as np
import numpy as np
import os
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Conv1D, MaxPooling1D, Flatten, Dense, Dropout
from tensorflow.keras.callbacks import EarlyStopping
import joblib

print("🔍 Loading augmented data...")
X = np.load("D:\pwave detector\dataset\X_balanced.npy")  # shape: (200, 120, 1)
y = np.load("D:\pwave detector\dataset\y_balanced.npy")  # shape: (200,)

print("📏 Scaling input...")
X = X.reshape(X.shape[0], -1)  # Flatten for scaler
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)
X_scaled = X_scaled.reshape(-1, 120, 1)  # Reshape back

print(f"✅ X shape: {X_scaled.shape}, y shape: {y.shape}")

X_train, X_val, y_train, y_val = train_test_split(X_scaled, y, test_size=0.2, random_state=42)

print("🧠 Building model...")
model = Sequential([
    Conv1D(16, kernel_size=5, activation='relu', input_shape=(120, 1)),
    MaxPooling1D(pool_size=2),
    Dropout(0.2),

    Conv1D(32, kernel_size=3, activation='relu'),
    MaxPooling1D(pool_size=2),
    Dropout(0.2),

    Flatten(),
    Dense(32, activation='relu'),
    Dropout(0.3),
    Dense(1, activation='sigmoid')
])

model.compile(optimizer='adam', loss='binary_crossentropy', metrics=['accuracy'])

print("🚀 Training model...")
model.fit(
    X_train, y_train,
    epochs=30,
    batch_size=16,
    validation_data=(X_val, y_val),
    callbacks=[EarlyStopping(patience=5, restore_best_weights=True)],
    verbose=1
)

# Save model and scaler
os.makedirs("models", exist_ok=True)
model.save("models/pwave_cnn_model.keras")
joblib.dump(scaler, "models/pwave_scaler.pkl")
print("✅ Model saved to models/pwave_cnn_model.keras")
print("✅ Scaler saved to models/pwave_scaler.pkl")
