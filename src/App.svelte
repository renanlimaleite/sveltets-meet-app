<script lang="ts">
  import Header from "./ui/Header.svelte";
  import MeetupGrid from "./Meetups/MeetupGrid.svelte";

  const meetups = [
    {
      id: 'm1',
      title: 'Coding Bootcamp',
      subtitle: 'Learn to code in 2 hours',
      description: 'In this meetup, we will have some experts to learn',
      imageUrl: 'https://2e8ram2s1li74atce18qz5y1-wpengine.netdna-ssl.com/wp-content/uploads/2019/01/Bootcamp-MOOC-Learning-Tech-Coding-Programming-Dice-1024x640.png',
      address: 'Rua do Acre - Centro - Rio de Janeiro - RJ',
      contact: 'code@test.com'
    },
    {
      id: 'm2',
      title: 'Swim together',
      subtitle: 'Lets swim together',
      description: 'In this meetup, we will have some swim',
      imageUrl: 'https://2e8ram2s1li74atce18qz5y1-wpengine.netdna-ssl.com/wp-content/uploads/2019/01/Bootcamp-MOOC-Learning-Tech-Coding-Programming-Dice-1024x640.png',
      address: 'Rua 1º de Março - Centro - Rio de Janeiro - RJ',
      contact: 'swim@test.com'
    }
  ]
</script>

<Header />

<main>
  <MeetupGrid {meetups} />
</main>

<style>
  main {
    margin-top: 5rem;
  }
</style>