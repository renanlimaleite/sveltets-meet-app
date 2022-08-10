<script lang="ts">
  import { createEventDispatcher } from "svelte";
  import TextInput from "../ui/TextInput.svelte";
  import Button from "../ui/Button.svelte";

  type typeDispatch = {
    [key: string]: {
      title: string
      subtitle: string
      address: string
      email: string
      description: string
      imageUrl: string
    }
  }

  const dispatch = createEventDispatcher<typeDispatch>()

  let title = ''
  let subtitle = ''
  let address = ''
  let email = ''
  let description = ''
  let imageUrl = ''

  function submitForm(event: Event) {
    event.preventDefault()

    dispatch('save', {
      title,
      subtitle,
      address,
      email,
      description,
      imageUrl
    })

  }
</script>

<!-- <form on:submit|preventDefault={addMeetup}> -->
<form on:submit={submitForm}>

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


<style>
  form {
    width: 30rem;
    max-width: 90%;
    margin: auto;
  }
</style>