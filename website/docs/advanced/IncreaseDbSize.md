---
id: db_size
title: Increasing Storage size
sidebar_label: Storage space increase
---


**Supported platforms:**
<PlatformSupport title="Android" platformIcon="icon_android.svg"></PlatformSupport>

---

Current Async Storage's size is set to 6MB. Going over this limit causes `database or disk is full` error. This 6MB limit is a sane limit to protect the user from the app storing too much data in the database. This also protects the database from filling up the disk cache and becoming malformed (endTransaction() calls will throw an exception, not rollback, and leave the db malformed). You have to be aware of that risk when increasing the database size. We recommend to ensure that your app does not write more data to AsyncStorage than space is left on disk. Since AsyncStorage is based on SQLite on Android you also have to be aware of the [SQLite limits](https://www.sqlite.org/limits.html).

### Increase limit

Add a `AsyncStorage_db_size_in_MB` property to your `android/gradle.properties`:

```bash
AsyncStorage_db_size_in_MB=10
```

Now you can define the new size in MB. In this example, the new limit is 10 MB.

<!-- ------------------------ COMPONENTS ------------------------ -->

export const PlatformSupport = ({platformIcon, title}) => (
    <div style={{
        display: 'flex',
        margin: '10px 20px',
        alignItems: 'center',
        flexDirection: 'row'
    }}>
      <img
       style={{width: 34, height: 34}}
       src={`/async-storage/img/${platformIcon}`} />
      <p style={{margin: '0 0 0 10px', padding: 0}}>{title}</p>
    </div>
  );
