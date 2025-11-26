---
id: getting-started
title: Introduction
description: This helpful guide lays out the prerequisites for learning React Native, using these docs, and setting up your environment.
---

import Tabs from '@theme/Tabs'; import TabItem from '@theme/TabItem'; import constants from '@site/core/TabsConstants';

<div className="content-banner">
  Welcome to the very start of your React Native journey! If you're looking for getting started instructions, they've moved to <a href="environment-setup">their own section</a>. Continue reading for an introduction to the documentation, Native Components, React, and more!
  <img className="content-banner-img" src="/docs/assets/p_android-ios-devices.svg" alt=" " />
</div>

Many different kinds of people use React Native: from advanced iOS developers to React beginners, to people getting started programming for the first time in their career. These docs were written for all learners, no matter their experience level or background.

## How to use these docs

You can start here and read through these docs linearly like a book; or you can read the specific sections you need. Already familiar with React? You can skip [that section](intro-react)—or read it for a light refresher.

## Prerequisites

To work with React Native, you will need to have an understanding of JavaScript fundamentals. If you’re new to JavaScript or need a refresher, you can [dive in](https://developer.mozilla.org/en-US/docs/Web/JavaScript) or [brush up](https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript) at Mozilla Developer Network.

:::info
While we do our best to assume no prior knowledge of React, Android, or iOS development, these are valuable topics of study for the aspiring React Native developer. Where sensible, we have linked to resources and articles that go more in depth.
:::

## Interactive examples

This introduction lets you get started immediately in your browser with interactive examples like this one:

```SnackPlayer name=Hello%20World
import React from 'react';
import {Text, View} from 'react-native';

const YourApp = () => {
  return (
    <View
      style={{
        flex: 1,
        justifyContent: 'center',
        alignItems: 'center',
      }}>
      <Text>Try editing me! 🎉</Text>
    </View>
  );
};

export default YourApp;
```

The above is a Snack Player. It’s a handy tool created by Expo to embed and run React Native projects and share how they render in platforms like Android and iOS. The code is live and editable, so you can play directly with it in your browser. Go ahead and try changing the "Try editing me!" text above to "Hello, world!"

:::tip
Optionally, if you want to set up a local development environment, [you can follow our guide to setting up your environment on your local machine](set-up-your-environment) and paste the code examples into your project. (If you are a web developer, you may already have a local environment set up for mobile browser testing!)
:::

## Developer Notes

People from many different development backgrounds are learning React Native. You may have experience with a range of technologies, from web to Android to iOS and more. We try to write for developers from all backgrounds. Sometimes we provide explanations specific to one platform or another like so:

<Tabs groupId="guide" queryString defaultValue="web" values={constants.getDevNotesTabs(["android","ios","web"])}>

<TabItem value="android">

:::info
Android developers may be familiar with this concept.
:::

</TabItem>
<TabItem value="ios">

:::info
iOS developers may be familiar with this concept.
:::

</TabItem>
<TabItem value="web">

:::info
Web developers may be familiar with this concept.
:::

</TabItem>
</Tabs>

## Formatting

Menu paths are written in bold and use carets to navigate submenus. Example: **Android Studio > Preferences**

---

Now that you know how this guide works, it's time to get to know the foundation of React Native: [Native Components](intro-react-native-components.md).
import React, { useEffect, useState } from 'react';
const t = {id: uid('t_'), title: newTaskTitle.trim(), description: newTaskDesc.trim(), status: 'todo', assignees: newTaskAssignee? [newTaskAssignee] : []};
setState(prev=> ({...prev, tasks: [...prev.tasks, t]}));
setNewTaskTitle(''); setNewTaskDesc(''); setNewTaskAssignee('');
}


// Drag & drop handlers (simple)
function onDragStart(e, taskId){
e.dataTransfer.setData('text/plain', taskId);
}
function onDragOver(e){ e.preventDefault(); }
function onDrop(e, newStatus){
const id = e.dataTransfer.getData('text/plain');
setState(prev=> ({...prev, tasks: prev.tasks.map(t=> t.id===id ? {...t, status: newStatus} : t)}));
}


const cols = [
{key: 'todo', title: 'Do zrobienia'},
{key: 'inprogress', title: 'W trakcie'},
{key: 'done', title: 'Zrobione'},
];


return (
<div className="min-h-screen bg-slate-100 p-6">
<div className="max-w-7xl mx-auto">
<Header onOpenAddMember={()=>setAddOpen(true)} />


<div className="mt-6 grid grid-cols-1 lg:grid-cols-4 gap-6">
<div className="lg:col-span-1">
<MemberList members={state.members} onSelect={(m)=> setSelectedMember(m)} />
<div className="mt-4 p-4 bg-white border rounded-lg">
<h4 className="font-semibold mb-2">Nowe zadanie</h4>
<input value={newTaskTitle} onChange={(e)=>setNewTaskTitle(e.target.value)} placeholder="Tytuł" className="w-full p-2 border rounded mb-2" />
<input value={newTaskAssignee} onChange={(e)=>setNewTaskAssignee(e.target.value)} placeholder="Przypisany (imię)" className="w-full p-2 border rounded mb-2" />
<textarea value={newTaskDesc} onChange={(e)=>setNewTaskDesc(e.target.value)} placeholder="Opis" className="w-full p-2 border rounded mb-2" />
<button onClick={addTask} className="w-full py-2 bg-emerald-500 text-white rounded">Dodaj zadanie</button>
</div>
</div>


<div className="lg:col-span-3">
<div className="flex gap-4">
{cols.map(c=> (
<div key={c.key} className="flex-1">
<Column
title={c.title}
tasks={state.tasks.filter(t=>t.status===c.key)}
onDragOver={onDragOver}
onDrop={(e)=>onDrop(e, c.key)}
onDragStart={onDragStart}
/>
</div>
))}
</div>
</div>
</div>


{/* Member detail / add modal */}
{isAddOpen && (
<div className="fixed inset-0 bg-black/40 flex items-center justify-center p-4">
<div className="w-full max-w-md bg-white rounded-lg p-6">
<h3 className="text-lg font-semibold mb-3">Dodaj członka</h3>
<input value={newMemberName} onChange={(e)=>setNewMemberName(e.target.value)} placeholder="Imię i nazwisko" className="w-full p-2 border rounded mb-2" />
<input value={newMemberRole} onChange={(e)=>setNewMemberRole(e.target.value)} placeholder="Rola (np. Frontend)" className="w-full p-2 border rounded mb-4" />
<div className="flex gap-2 justify-end">
<button onClick={()=>setAddOpen(false)} className="px-3 py-2">Anuluj</button>
<button onClick={addMember} className="px-3 py-2 bg-indigo-600 text-white rounded">Dodaj</button>
</div>
</div>
</div>
)}


{selectedMember && (
<div className="fixed bottom-6 right-6 w-80 bg-white border rounded-lg p-4 shadow-lg">
<div className="flex items-start justify-between">
<div>
<div className="text-lg font-semibold">{selectedMember.name}</div>
<div className="text-sm text-slate-500">{selectedMember.role}</div>
</div>
<div>
<button onClick={()=> removeMember(selectedMember.id)} className="text-sm text-red-600">Usuń</button>
</div>
</div>
<div className="mt-3 text-xs text-slate-500">Kliknij poza kartą aby zamknąć</div>
<div className="mt-3 flex justify-end">
<button onClick={()=> setSelectedMember(null)} className="px-3 py-1 rounded bg-slate-100">Zamknij</button>
</div>
</div>
)}


</div>
</div>
);
}
