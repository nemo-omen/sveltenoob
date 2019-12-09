---
layout: blog
title: Rendering nested objects in Svelte
date: Sunday, December 8, 2019
description: It's really, really easy to render nested objects in Svelte.
thumbnail: /uploads/sodapopinski.jpg
---
_This post originally appeared on [dev.to](https://dev.to/trainingmontage/rendering-nested-objects-in-svelte-9mh)_

Hi.

Total beginner here.

I've been re-learning some basic web development over the past few weeks and, along with vanilla JS, I've been working on a project in Svelte. One of the stumbling blocks for me was iterating through nested objects — actually, objects inside arrays ... inside objects ... inside arrays.

This may have been completely obvious to most people working with JavaScript or Svelte but, as a newbie, the way Svelte makes iterating through nested objects *so* easy came as a revelation.

Let's pretend we have an array of *Real Jabronis* in our code, those Jabronis carry with them an array of *Lame Moves*.
```javascript
const realJabronis = [
		{
			name: 'Soda Popinski',
			age: 43,
			height: '6\'5"',
			lameMoves: [
				{
					name: 'Triple Trotting Jab',
					power: 0.5,
					delay: 0.3
				},
				{
					name: 'Just an Uppercut',
					power: 0.9,
					delay: 0.6
				}
			]
		},
		{
			name: 'Kin Corn Karn',
			age: 35,
			height: '5\'11"',
			lameMoves: [
				{
					name: 'Mongolian Chop',
					power: 0.5,
					delay: 0.4
				},
				{
					name: 'Karate Kick',
					power: 0.9,
					delay: 0.6
				}
			]
		}
	];
```

Now let's pretend we're training an up-and-coming fighter and they need a list of the *Lame Moves* they need to train for if they want to fight these *Real Jabronis*. Svelte makes this **stupid easy**:

```html
{#each realJabronis as realJabroni}
	<h1>{realJabroni.name}</h1>
	<h2>Lame Moves to Train For</h2>
	{#each realJabroni.lameMoves as lameMove}
		<h3>Move Name: {lameMove.name}</h3>
		<p><strong>Power: {lameMove.power}</strong></p>
		<p><strong>Delay: {lameMove.delay}</strong></p>
	{/each}
{/each}
```

And you basically get exactly what you need.

![Some Real Jabronis](/images/nesting-example.jpg)

You can also, if you want to use components in these iterations (and you know you do,) pass each of these iteration levels into your component through props:

```html
{#each realJabronis as realJabroni}
	<RealJabroni name={realJabroni.name} lameMoves={realJabroni.lameMoves} />
{/each}
```

And, of course, `export let lameMoves = [];` from inside `RealJabronis.svelte` will give you a nice array to work with.

**What tips do you have for iterating through nested objects and arrays in Vanilla JS?**