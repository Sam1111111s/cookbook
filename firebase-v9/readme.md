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

### Collection reference
```
import { collection } from 'firebase/firestore';

collection(db,'collection_name')
```
### get documents data (Read)
```
import { getDocs } from 'firebase/firestore';

const colRef = collection(db,'collection_name')
getDocs(colRef)
    .then((snapshot)=>{
        let arr = []
        snapshot.docs.forEach((doc)=>{
            books.push({...doc.data()})
        })
    })
    .catch(err=>console.log(err))
```

### Adding (Create)
```

```
### Deleting 
```

```
### Edit (Update)
```

```