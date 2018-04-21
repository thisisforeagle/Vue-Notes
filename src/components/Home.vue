<template>
  <div class="outerContainer">
    <h1>Darragh's Notes</h1>

    <button type="button" class="btn btn-secondary btn-outline btn-sm" data-toggle="modal" data-target="#myModal">Add New Note</button>

    <div class="noteContainer">
      <div class="card" :class="note.size" v-for="note, index in notes" data-toggle="modal" data-target="#editModal">
        <h3 class="lead float-left" @click="editNote(index)">{{ note.title }}</h3>
          <img :src="note.image" alt="Avatar" style="width:100%" v-show="note.image" @click="editNote(index)">
          <p @click="editNote(index)">{{ note.content }}</p>
      </div>
    </div>

    <!-- New Note Modal -->
    <div id="myModal" class="modal fade" role="dialog" v-show="modal">
      <div class="modal-dialog">

        <!-- Modal content-->
        <div class="modal-content">
          <div class="modal-header">
            <button type="button" class="close" data-dismiss="modal" @click="$emit('close')">&times;</button>
            <h4 class="modal-title">Add new note</h4>
          </div>
          <div class="modal-body">
            <form class="newNoteForm">
              <div class="form-group">
                <label>Title:</label>
                <input type="text" class="form-control" id="title" v-model="newnote.title">
              </div>
              <div class="form-group">
                <label>Image:</label>
                <input type="text" class="form-control" id="image" v-model="newnote.image">
              </div>
              <div class="form-group">
                <label>Content:</label>
                <textarea type="text" class="form-control" id="content" v-model="newnote.content"></textarea>
              </div>

              <button class="btn btn-small btn-secondary clearfix float-center" @click.prevent="addNote">Add Note</button>

            </form>
          </div>
        </div>

      </div>
    </div>
    <!-- Edit Note Modal -->
    <div id="editModal" class="modal fade" role="dialog" v-show="editmodal">
      <div class="modal-dialog">

        <!-- Modal content-->
        <div class="modal-content">
          <div class="modal-header">
            <button type="button" class="close" data-dismiss="modal" @click="">&times;</button>
            <h4 class="modal-title">Edit note</h4>
          </div>
          <div class="modal-body">
            <form class="newNoteForm">
              <div class="form-group">
                <label>Title:</label>
                <input type="text" class="form-control" id="title" v-model="editnote.title">
              </div>
              <div class="form-group">
                <label>Image:</label>
                <input type="text" class="form-control" id="image" v-model="editnote.image">
              </div>
              <div class="form-group">
                <label>Content:</label>
                <textarea type="text" class="form-control" id="content" v-model="editnote.content"></textarea>
              </div>

              <button class="btn btn-secondary btn-small clearfix" @click.prevent="$emit('close')">Add Note</button>

            </form>
          </div>
        </div>

      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: 'home',
  data() {
      return {
        msg: 'Welcome to Darraghs Note app',
        images: '',
        newnote: {},
        editnote: {},
        modal: false,
        editmodal: false,
        notes: [
          {
            title: 'Welcome to DarraghKing.ie',
            image: 'https://images.unsplash.com/photo-1495594059084-33752639b9c3?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=ab5c208787458272964e09fb4c19cb1f&auto=format&fit=crop&w=1600&q=80',
            content: 'Just a simple site to host some recent projects, and javascript snippets i have been working on.',
            link: '#'
          }
        ]
      }
    },
    methods: {
      addNote: function () {
        this.notes.push(this.newnote);
        this.newnote = {};
        $emit('close')
      },
      deleteNote: function (index) {
        this.notes.splice(index, 1);
      },
      editNote: function () {
        console.log('Edit note!');
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h1,
  h2 {
    font-weight: normal;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    display: inline-block;
    margin: 0 10px;
  }

  a {
    color: #42b983;
  }
  .outerContainer {
    margin-top: 2%;
  }
  .noteContainer {
    column-count: 4;
    column-gap: 1em;
    padding: 0;
    -moz-column-gap: 1.5em;
    -webkit-column-gap: 1.5em;
    column-gap: 1.5em;
    font-size: .85em;
    margin: 5%;
  }
  @media only screen and (max-width: 870px) {
    .noteContainer {
      column-count: 3;
    }
  }
  @media only screen and (max-width: 650px) {
    .noteContainer {
      column-count: 2;
    }
  }
  @media only screen and (max-width: 430px) {
    .noteContainer {
      column-count: 1;
    }
  }

  .card {
    /* Add shadows to create the "card" effect */
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    transition: 0.3s;
    padding: 5%;
    display: inline-block;
    width: 100%;
    margin-bottom: 25px;
  }

  /* On mouse-over, add a deeper shadow */

  .card:hover {
    box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
    cursor: pointer;
  }

  h3.lead {
    max-width: 93%;
    text-align: left;
    overflow-wrap: break-word;
  }

  #newNote {
    width: 35%;
    position: fixed;
    top: 20%;
  }

  .newNoteForm {
    width: 100%;
    padding: 5%;
    background: white;
  }

  .close {
    position: absolute;
    top: 20px;
    right: 20px;
  }
</style>
