Explanation of Each Folder
1️⃣ Presentation Layer (UI & State)

    screens/ → Flutter UI screens (e.g., home_screen.dart)

    widgets/ → Reusable UI components (e.g., custom_button.dart)

    state/ → State management (e.g., BLoC, Cubit, Provider)

    routes/ → App navigation setup

    utils/ → UI-related helper functions

2️⃣ Domain Layer (Business Logic - Independent of Flutter)

    entities/ → Core business objects (e.g., UserEntity)

    usecases/ → Contains app logic (e.g., GetUserProfile)

    repositories/ → Abstract contract for data sources

3️⃣ Data Layer (Handles API & Local Storage)

    models/ → JSON-convertible models (extends entities)

    datasources/ → Handles fetching/storing data

    local/ → Local database like SQLite, Hive

    remote/ → API calls using HTTP, Firebase

    repositories/ → Implements domain repositories

4️⃣ Core Module (Reusable Utilities)

    error/ → Custom exceptions & failure handling

    network/ → API client configurations

    usecases/ → Base class for use cases

    utils/ → Common utilities like constants, formatters

Visual Structure
📂 lib/
 ┣ 📂 core/ (Reusable Utilities)
 ┃  ┣ 📂 error/ (Custom exceptions & failure handling)
 ┃  ┣ 📂 network/ (API client configurations)
 ┃  ┣ 📂 usecases/ (Base class for use cases)
 ┃  ┗ 📂 utils/ (Common utilities like constants, formatters)
 ┣ 📂 data/ (Handles API & Local Storage)
 ┃  ┣ 📂 models/ (JSON-convertible models, extends entities)
 ┃  ┣ 📂 datasources/ (Handles fetching/storing data)
 ┃  ┃  ┣ 📂 local/ (Local database like SQLite, Hive)
 ┃  ┃  ┗ 📂 remote/ (API calls using HTTP, Firebase)
 ┃  ┗ 📂 repositories/ (Implements domain repositories)
 ┣ 📂 domain/ (Business Logic - Independent of Flutter)
 ┃  ┣ 📂 entities/ (Core business objects (e.g., UserEntity))
 ┃  ┣ 📂 usecases/ (Contains app logic (e.g., GetUserProfile))
 ┃  ┗ 📂 repositories/ (Abstract contract for data sources)
 ┣ 📂 presentation/ (UI & state management)
 ┃  ┣ 📂 pages/ (App screens)
 ┃  ┣ 📂 widgets/ (Reusable components)
 ┃  ┣ 📂 state/ (BLoC/Cubit for state management)
 ┃  ┣ 📂 utils/ (UI-related helper functions)
 ┃  ┗ 📂 routes/ (Navigation setup)
 ┗ main.dart


Cases to Case
1️⃣ Where to Place a Data Class for "Properties"?
A data class that represents a "card" with properties like 
cardType, cardNumber, cardExpiration, and userName is considered a core business object.

📌 Placement in Architecture:

- If the card is a core entity (used across multiple features):
lib/domain/entities/card_entity.dart

- If the card data model includes JSON conversion (for APIs or databases):
lib/data/models/card_model.dart

Structure
📂 domain/
 ┣ 📂 entities/
 ┃ ┗ 📜 card_entity.dart (Defines business rules for Card)
📂 data/
 ┣ 📂 models/
 ┃ ┗ 📜 card_model.dart (Includes JSON conversion)


2️⃣ If Project Has No Database or API? What Folders Should I Use?
If project doesn't use a database or API, you don't need the data/ layer.
You only need presentation and domain layers.

Structure
📂 lib/
 ┣ 📂 core/ (For common utilities)
 ┣ 📂 domain/ (Contains business logic)
 ┃ ┣ 📂 entities/ (Core business models)
 ┃ ┗ 📂 usecases/ (Business logic implementation)
 ┗ 📂 presentation/ (UI & state management)
   ┣ 📂 screens/ (App screens)
   ┣ 📂 widgets/ (Reusable components)
   ┣ 📂 state/ (BLoC/Cubit for state management)
   ┗ 📂 routes/ (Navigation setup)
