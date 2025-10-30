
# 🛍️ Flutter E-Commerce App

A modern **E-Commerce mobile app** built with **Flutter**, designed to showcase clean architecture, reusable components, and a smooth user experience for both Android and iOS.  
This project demonstrates my ability to structure, scale, and deliver production-ready Flutter apps.

---

## 🚀 Features

- Beautiful, responsive UI built with **Flutter 3+**
- Follows **Clean Architecture** and **MVVM principles**
- Uses **Riverpod** for state management
- Integrated **theme switching (Light & Dark Mode)**
- **Navigation**, **form validation**, and **custom animations**
- Modularized components for **products**, **cart**, **checkout**, and **user profile**
- Ready for integration with **REST APIs** or **Firebase backend**

---

## 🧩 Project Structure


lib/
│
├── core/               # Constants, themes, routes
├── data/               # Models, repositories
├── modules/
│   ├── auth/           # Login, Signup, Forgot Password
│   ├── home/           # Home screen, product listings
│   ├── cart/           # Cart & checkout flow
│   ├── profile/        # User profile & settings
│   └── widgets/        # Shared UI components
└── main.dart


---

## 🛠️ Tech Stack

| Category           | Tools                                      |
|--------------------|--------------------------------------------|
| Framework          | Flutter (Dart)                             |
| State Management   | **Riverpod** (with hooks & async notifiers) |
| Architecture       | Clean Architecture, MVVM                   |
| Backend (Optional) | Firebase / REST API                        |
| UI/UX              | Material Design 3, Responsive Layouts      |
| Version Control    | Git & GitHub                               |

---

## 📱 Screenshots

| Home | Product Details | Cart | Profile |
|------|-----------------|------|----------|
| ![Home](readme_image/home.png) | ![Product](readme_image/product.png) | ![Cart](readme_image/cart.png) | ![Profile](readme_image/profile.png) |

---

## 🧠 What This Project Demonstrates

- Building **scalable Flutter apps** with modular design  
- Managing state effectively using **Riverpod** (no BuildContext dependency)
- Applying **clean code principles** and **design patterns**  
- Creating **reusable widgets** and **responsive layouts**  
- Implementing **real-world e-commerce flows**

---

## ⚙️ Getting Started

```bash
git clone https://github.com/yourusername/ecommerce-flutter.git
cd ecommerce-flutter
flutter pub get
flutter run
```

---

## 🧪 Folder-by-Folder Overview

### `core/`
> Constants, themes, routes, and shared utilities used across the app.

### `data/`
> Houses models and repositories — clean separation between UI and data logic.

### `modules/`
> Each feature (auth, home, cart, profile) is a self-contained module with:
> - `controller/` → Riverpod providers & notifiers  
> - `view/` → UI screens  
> - `widgets/` → Local reusable components

### `widgets/`
> Global reusable UI components (buttons, cards, loaders, etc.).

---

## 💡 Riverpod State Management Example

### Product List Notifier (Async Loading)

```dart
final productListProvider = AutoDisposeAsyncNotifierProvider<ProductListNotifier, List<Product>>(() {
  return ProductListNotifier();
});

class ProductListNotifier extends AutoDisposeAsyncNotifier<List<Product>> {
  @override
  Future<List<Product>> build() async {
    state = const AsyncLoading();
    final repository = ref.read(productRepositoryProvider);
    return await repository.fetchProducts();
  }

  Future<void> refresh() => future;
}
```

### Using in UI (Hook Widget)

```dart
class ProductListView extends HookConsumerWidget {
  @override
  Widget build(BuildContext context, WidgetRef ref) {
    final asyncProducts = ref.watch(productListProvider);

    return asyncProducts.when(
      loading: () => const CircularProgressIndicator(),
      error: (err, _) => Text('Error: $err'),
      data: (products) => ListView.builder(
        itemCount: products.length,
        itemBuilder: (context, index) => ProductCard(product: products[index]),
      ),
    );
  }
}
```

---

## 📘 Key Learnings / Focus Areas

- **Riverpod** for scalable, testable state management  
- Following **SOLID** and **Clean Architecture** principles  
- Building **production-quality UIs** with Material 3  
- Integrating APIs and managing **asynchronous data flow**  
- Maintaining **readable, scalable, and testable** code

---

## 👨‍💻 Author

**Your Name**  
📧 [your.email@example.com](mailto:your.email@example.com)  
🔗 [LinkedIn](https://linkedin.com/in/yourprofile) | [GitHub](https://github.com/yourusername)

---

## 🧾 License

This project is licensed under the **MIT License** — feel free to use and modify.

---

> 🎯 **Goal:** This project was built to demonstrate full lifecycle Flutter app development — from design and architecture to delivery — suitable for showcasing professional readiness during interviews or technical assessments.

```

---
**Ready to impress?** Replace placeholder images, update your name/GitHub, and pair this with a live demo or video walkthrough for maximum impact!
```
