<script lang="ts">
  import Header from "./ui/Header.svelte";
  import MeetupGrid from "./Meetups/MeetupGrid.svelte";
  import TextInput from './ui/TextInput.svelte';
  import Button from './ui/Button.svelte';

  let meetups = [
    {
      id: 'm1',
      title: 'Coding Bootcamp',
      subtitle: 'Learn to code in 2 hours',
      description: 'In this meetup, we will have some experts to learn',
      imageUrl: 'https://2e8ram2s1li74atce18qz5y1-wpengine.netdna-ssl.com/wp-content/uploads/2019/01/Bootcamp-MOOC-Learning-Tech-Coding-Programming-Dice-1024x640.png',
      address: 'Rua do Acre - Centro - Rio de Janeiro - RJ',
      contact: 'code@test.com',
      favorite: false,
    },
    {
      id: 'm2',
      title: 'Swim together',
      subtitle: 'Lets swim together',
      description: 'In this meetup, we will have some swim',
      imageUrl: 'https://2e8ram2s1li74atce18qz5y1-wpengine.netdna-ssl.com/wp-content/uploads/2019/01/Bootcamp-MOOC-Learning-Tech-Coding-Programming-Dice-1024x640.png',
      address: 'Rua 1º de Março - Centro - Rio de Janeiro - RJ',
      contact: 'swim@test.com',
      favorite: false,
    }
  ]

  let title = ''
  let subtitle = ''
  let address = ''
  let email = ''
  let description = ''
  let imageUrl = ''
   
  function addMeetup(event: SubmitEvent) {
    event.preventDefault()

    const newMeetUp = {
      id: Math.random().toString(),
      title,
      subtitle,
      description,
      imageUrl,
      address,
      contact: email,
      favorite: false
    }
    
    
    meetups = [...meetups, newMeetUp]
  }
  
  function handleInput(e: Event) {
    const target = e.target as HTMLInputElement;
    console.log(target.id)
    console.log(target.value)
    target.id = target.value
  }

  function toggleFavorite(event: CustomEvent<string>) {
    const id = event.detail    
    meetups = meetups.map(meet => {
      if (meet.id === id) {
        return {
          ...meet,
          favorite: !meet.favorite
        }
      } else {
        return {
          ...meet
        }
      }
    })
    console.log(meetups)
  }
</script>

<Header />

<main>
  <!-- <form on:submit|preventDefault={addMeetup}> -->
  <form on:submit={addMeetup}>

    <TextInput
      id="title"
      label="Title"
      controlType="text"      
      bind:value={title}
    />
    
    <TextInput
      id="subtitle"
      label="Subtitle"
      controlType="text"
      bind:value={subtitle}
    />

    <TextInput
      id="address"
      label="Address"
      controlType="text"
      bind:value={address}
    /> 

    <TextInput
      id="imageUrl"
      label="Image Url"
      controlType="text"
      bind:value={imageUrl}
    />

    <TextInput
      id="email"
      label="E-mail"
      controlType="text"
      type="email"
      bind:value={email}
    />

    <TextInput
      id="description"
      label="Description"
      controlType="textarea"
      bind:value={description}
    />

    <Button type="submit" caption="Save" />
  </form>
  <MeetupGrid {meetups} on:togglefavorite={toggleFavorite} />
</main>

<style>
  main {
    margin-top: 5rem;
  }

  form {
    width: 30rem;
    max-width: 90%;
    margin: auto;
  }
</style>