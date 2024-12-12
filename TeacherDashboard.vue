<template>
  <div class="teacher-dashboard">
    <div class="header">
      <h1 class="app-title">DataHive</h1>
    </div>
    <div class="content">
      <div class="left-section">
        <h2>File Upload</h2>
        <div class="file-upload">
          <div>
            <input type="file" @change="uploadFile" />
            <input type="text" v-model="textToUpload" placeholder="Enter text to upload" />
            <button @click="uploadFileAndText">Upload</button>
          </div>
        </div>
        <div class="uploaded-items">
          <h3>Uploaded Items</h3>
          <div v-for="item in uploadedItems" :key="item.id" class="uploaded-item">
            <div>{{ item.fileName }} ({{ item.fileType }})</div>
            <div>Uploaded at: {{ item.uploadedAt }}</div>
            <button @click="deleteItem(item.id)">Delete</button>
          </div>
        </div>
      </div>
      <div class="right-section">
        <div class="interaction-result-box">
          <h3>Retrieved Answer</h3>
          <div class="retrieved-answer">{{ interactionResult }}</div>
        </div>
        <div class="text-interaction">
          <input type="text" v-model="textToInteract" placeholder="Enter text to interact" />
          <button @click="interactWithText">Submit</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TeacherDashboard',
  data() {
    return {
      username: 'John Doe',
      textToUpload: '',
      uploadedItems: [],
      textToInteract: '',
      interactionResult: ''
    };
  },
  methods: {
    uploadFile(event) {
      // Handle file upload
      // Call backend API to upload the file
    },
    uploadFileAndText() {
      // Handle file and text upload
      // Call backend API to upload the file and text
      this.uploadedItems.push({
        id: this.uploadedItems.length + 1,
        fileName: this.textToUpload,
        fileType: 'text',
        uploadedAt: new Date().toLocaleString()
      });
      this.textToUpload = '';
    },
    deleteItem(id) {
      // Handle item deletion
      // Call backend API to delete the file or text
      this.uploadedItems = this.uploadedItems.filter(item => item.id !== id);
    },
    interactWithText() {
      // Handle text interaction
      // Call backend API to interact with the text
      // Update the interactionResult based on the response
      this.interactionResult = 'Interaction result goes here';
      this.textToInteract = '';
    }
  }
};
</script>

<style scoped>
.teacher-dashboard {
  display: flex;
  flex-direction: column;
  gap: 20px;
  background-color: #121212;
  color: #ffffff;
}

.header {
  text-align: center;
  padding: 20px 0;
  background-color: #1f1f1f;
}

.app-title {
  font-size: 2.5rem;
  font-weight: bold;
  color: #ffffff;
}

.content {
  display: flex;
  gap: 20px;
}

.left-section,
.right-section {
  flex: 1;
  padding: 20px;
  background-color: #1e1e1e;
  border: 1px solid #333;
  border-radius: 8px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.file-upload input[type="file"] {
  margin-bottom: 10px;
  background-color: #2c2c2c;
  color: #ffffff;
  border: none;
  border-radius: 4px;
  padding: 5px;
}

.file-upload input[type="text"] {
  margin-bottom: 10px;
  background-color: #2c2c2c;
  color: #ffffff;
  border: 1px solid #555;
  border-radius: 4px;
  padding: 5px;
}

.file-upload button {
  background-color: #3a3a3a;
  color: #ffffff;
  border: none;
  border-radius: 4px;
  padding: 5px 10px;
}

.uploaded-items .uploaded-item {
  margin: 10px 0;
  background-color: #2c2c2c;
  padding: 10px;
  border-radius: 4px;
}

.text-interaction {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.text-interaction input[type="text"] {
  background-color: #2c2c2c;
  color: #ffffff;
  border: 1px solid #555;
  border-radius: 4px;
  padding: 5px;
}

.text-interaction button {
  background-color: #3a3a3a;
  color: #ffffff;
  border: none;
  border-radius: 4px;
  padding: 5px 10px;
}

.interaction-result {
  background-color: #2c2c2c;
  color: #ffffff;
  padding: 20px;
  border-radius: 4px;
  font-size: 1.2rem;
  height: 200px;
  overflow-y: auto;
}

.interaction-result-box {
  margin-bottom: 20px;
  background-color: #2c2c2c;
  padding: 10px;
  border-radius: 4px;
}

.retrieved-answer {
  background-color: #1e1e1e;
  color: #ffffff;
  padding: 20px;
  border-radius: 4px;
  font-size: 1.2rem;
  min-height: 200px;
}
</style>
