# How to config firebase v9 for CRUD OPS

Create a config file *fbconfig.js*.
* Config app
* Config database

```
import { initializeApp } from "firebase/app";

//initialize database
import { getFirestore } from "firebase/firestore";
        
const firebaseConfig = {
    apiKey: " ",
    authDomain: " ",
    projectId: " ",
    storageBucket: " ",
    messagingSenderId: " ",
    appId: " ",
    measurementId: " "
}

const app = initializeApp(firebaseConfig)

//export database
export const db = getFirestore(app)
```

## Collection reference
```
import { collection } from 'firebase/firestore';

collection(db,'collection_name')
```
## Get documents data (Read)
```
import { getDocs } from 'firebase/firestore';

const colRef = collection(db,'collection_name')

getDocs(colRef)
    .then((snapshot)=>{
        console.log(snapshot)
    })


//////////////////// OR //////////////////////////

getDocs(colRef)
    .then((snapshot)=>{
        let arr = []
        snapshot.docs.forEach((doc)=>{
            books.push({...doc.data()})
        })
    })
    .catch(err=>console.log(err))
 
```

## Get single document
>*OnSnapShot is also applicable**
```
import { getDoc,doc } from 'firebase/firestore';

const docRef = doc(db, 'collection_name', 'doc_id')

getDoc(docRef)
    .then((doc)=>{
        console.log(doc.data(), doc.id)
    })


```

## Real-time Collection of data (Read)

```
import { onSnapShot } from "firebase/firestore"

const colRef = collection(db,'collection_name')

onSnapShot(colRef),(sanpshot)=>{
    let arr = []
    snapshot.docs.forEach((doc)=>{
        arr.push({...doc.data()})
    })
    console.log(arr)
}

```
>## Queries, Order (Read)
```
import { onSnapshot, query, where, orderBy } from "firebase/firestore"

const colRef = collection(db,'collection_name')

const q = query(colRef,where("param","==","item"), orderBy('param','asc'/'desc'))

onSnapShot(q),(sanpshot)=>{
    let arr = []
    snapshot.docs.forEach((doc)=>{
        arr.push({...doc.data()})
    })
    console.log(arr)
}

```


## Adding (Create)
```
import { addDoc } from "firebase/firestore"

const colRef = collection(db,'collection_name')
addDoc(colRef,{...data})
    .then(()=>{console.log('added data')})
    .catch((err)=>{console.log(err)})

```
## Deleting 
```
import { deleteDoc,doc } from "firebase/firestore"

const docRef = doc(db, 'collection_name', doc_id)

deleteDoc(docRef)
    .then(()=>{console.log('deleted data')})
    .catch((err)=>{console.log(err)})
    
```
## Edit (Update)
```
import { updateDoc,doc } from "firebase/firestore"

const docRef = doc(db, 'collection_name', doc_id)

updateDoc((docRef)=>{...newData})
    .then(()=>{console.log('updated')})
    .catch((err)=>{console.log(err)})
```