<h1  align="center" > 🍄 𝐑𝖾ᑯυ𝗑 𝐓ⱺⱺᥣ𝗄𝗂𝗍 🥠</h1>

</br>

<h3  align="center" >

Redux Toolkit is available as a package on NPM for use with a module bundler or in a Node application:

</h3>

</br>

```bash
npm install @reduxjs/toolkit react-redux

```

</br>

# 📦 What Is Store?

A store is a central place where the state of our application is stored.  
It can be created using the `configureStore` function and holds the entire state tree of our application.

</br>

## 🛠️ Step 1️⃣: Create Store

<p align="center">
   <img src="https://github.com/user-attachments/assets/d13207de-e1df-44c6-9938-837b4c227cee" width="750px" height="418px" />
</p>

</br>

## 🔗 Step 2️⃣: Provide the Redux Store to React

<p align="center">
   <img src="https://github.com/user-attachments/assets/fc2d41f0-e9b6-4468-aaad-41bed39cd02b" width="750px" height="748px" />
</p>

</br>

# 🍰 What Is Slice?

A **slice** is a piece of store state and the corresponding reducer logic to update that state.  
Slices help organize our Redux store by breaking it into smaller, more manageable parts.

</br>

## 🎂 Slices Analogy

Imagine you have a big cake 🎂, and you want to cut it into smaller, more manageable pieces.  
Each piece is like a **"slice"** of the cake.  

In Redux Toolkit, a **slice** represents a smaller part of your application's overall state,  
along with the instructions on how to update that specific part.

</br>

## ✂️ Step 3️⃣: Create Slice

<p align="center">
   <img src="https://github.com/user-attachments/assets/3f2f4ab8-90a5-467f-bde9-899133a9e808" width="750px" height="768px" />
</p>

</br>

## 🏁 initialState

- 🟢 **InitialState** is the starting point of our application's state.

</br>

## ⚙️ Reducers

- 📜 **Reducers** define how a particular slice of the store can be updated.  
- 🔄 Think of them as the **instructions** for modifying the state.

</br>

## 🎬 Actions

- ✅ **Actions** are commands that specify how a slice of state should be updated.  
- 🍽️ Example: You might have an action called **"Eat a Bite"**,  
   which updates a slice by reducing its size.

</br>

## 🔗 Step 4️⃣: Add Slice Reducers to the Store

<p align="center">
   <img src="https://github.com/user-attachments/assets/b887887e-93a0-47fa-be9e-f7b4219a088d" width="750px" height="481px" />
</p>

</br>

## ⚡Step 5️⃣: Use Redux State and Actions in React Components

<p align="center">
   <img src="https://github.com/user-attachments/assets/5a444966-08ee-4c5d-8be4-4177ac415309" width="750px" height="679px" />
</p>

</br>

## 🧐 useSelector( ) Hook

- 📥 `useSelector` allows us to **read** data from the Redux store.

</br>

## 🚀 useDispatch( ) Hook

- 🏗️ `dispatch` is used to send **actions** to the store,  
   triggering updates to the application state.
- 🔄 It enables components to interact with the store and modify the state dynamically.
