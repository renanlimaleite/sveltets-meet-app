<script lang="ts">
  import Header from "./ui/Header.svelte";
  import Button from "./ui/Button.svelte";
  import MeetupGrid from "./Meetups/MeetupGrid.svelte";
  import EditMeetup from './Meetups/EditMeetup.svelte';

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
  
  let editMode = false;

  type eventProps = {
    event: SubmitEvent
    title: string
    subtitle: string
    description: string
    imageUrl: string
    address: string
    contact: string
  } 
     
  function addMeetup(event: CustomEvent<eventProps>) {
    event.preventDefault()
            
    const newMeetUp = {
      id: Math.random().toString(),
      title: event.detail.title,
      subtitle: event.detail.subtitle,
      description: event.detail.description,
      imageUrl: event.detail.imageUrl,
      address: event.detail.address,
      contact: event.detail.contact,
      favorite: false
    }
    
    meetups = [newMeetUp, ...meetups]
    editMode = false
  }
  
  // function handleInput(e: Event) {
  //   const event.detail.subtitle
  //   console.log(target.id)
  //   console.log(target.value)
  //   target.id = target.value
  // }

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
  <div class="meetup-controls">
    <Button caption="New Meetup" on:click={() => editMode = !editMode} />
  </div>

  {#if editMode}
    <EditMeetup on:save={addMeetup} />
  {/if}

  <MeetupGrid {meetups} on:togglefavorite={toggleFavorite} />
</main>

<style>
  main {
    margin-top: 5rem;
  }

  .meetup-controls {
    margin: 1rem;
  }
</style>