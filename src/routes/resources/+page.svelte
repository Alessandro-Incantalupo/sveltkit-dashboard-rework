<!-- <script lang="ts">
  import CardSection from '$lib/components/card-section/CardSection.svelte';
  import Table from '$lib/components/common/Table.svelte';
  import UserContentControls from '$lib/components/forms/UserContentControls.svelte';
  import UploadDialog from '$lib/components/modals/UploadDialog.svelte';
  import HeaderControls from '$lib/components/tables/HeaderControls.svelte';
  import resources from '$lib/data/resources.json';
  import userContentAccess from '$lib/data/user-content-access.json';
  import { toast } from 'svelte-sonner';

  // Page state
  let data = $state(resources);
  let dataUsers = $state(userContentAccess);
  let activeTab = $state('All');
  let searchValue = $state('');
  let selectedProvider = $state('');

  // Upload dialog state
  let uploadDialogOpen = $state(false);
  let uploadForm = $state({
    title: '',
    description: '',
    category: '',
    language: '',
    provider: '',
    role: '',
    file: null
  });

  // Configuration
  const tabs = [
    { name: 'Stats', icon: 'ion:stats-chart-outline', active: false },
    { name: 'All', active: true },
    { name: 'Videos', active: false },
    { name: 'Documents', active: false },
    { name: 'Lessons', active: false },
    { name: 'Archive', active: false, disabled: true }
  ];

  const heads = ['Content Title', 'Path', 'View Count', 'Uploaded By', 'Provider', 'Type'];
  const headsUsers = ['User', 'Accessed Content', 'Opened on', 'Closed on', 'Provider'];

  const categoryOptions = [
    { label: 'Video', value: 'video' },
    { label: 'Document', value: 'document' },
    { label: 'Lesson', value: 'lesson' },
    { label: 'Tutorial', value: 'tutorial' }
  ];

  const languageOptions = [
    { label: 'English', value: 'english' },
    { label: 'Spanish', value: 'spanish' },
    { label: 'French', value: 'french' },
    { label: 'German', value: 'german' }
  ];

  const providerOptions = [
    { label: 'Pack', value: 'pack' },
    { label: 'Mentor', value: 'mentor' },
    { label: 'External', value: 'external' },
    { label: 'Internal', value: 'internal' },
    { label: 'Partner', value: 'partner' }
  ];

  const roleOptions = [
    { label: 'Mentor / Coach', value: 'mentor' },
    { label: 'Mentee / Coachee', value: 'mentee' }
  ];

  // Event handlers
  const handleTabClick = (tabName: string) => (activeTab = tabName);
  const handleUpload = () => (uploadDialogOpen = true);
  const handleDownload = () =>
    toast.success('Download started!', { duration: 3000, position: 'top-center' });

  const handleSubmitUpload = () => {
    toast.success('Resource Uploaded Successfully!', { duration: 3000, position: 'top-center' });
    uploadForm = {
      title: '',
      description: '',
      category: '',
      language: '',
      provider: '',
      role: '',
      file: null
    };
    uploadDialogOpen = false;
  };
</script>

<UploadDialog
  bind:open={uploadDialogOpen}
  bind:uploadTitle={uploadForm.title}
  bind:uploadDescription={uploadForm.description}
  bind:uploadCategory={uploadForm.category}
  bind:uploadLanguage={uploadForm.language}
  bind:uploadProvider={uploadForm.provider}
  bind:uploadRole={uploadForm.role}
  {categoryOptions}
  {languageOptions}
  {providerOptions}
  {roleOptions}
  onSubmit={handleSubmitUpload}
/>

<HeaderControls
  {tabs}
  {activeTab}
  bind:searchValue
  onTabClick={handleTabClick}
  onUpload={handleUpload}
/>

{#if activeTab === 'All'}
  <Table {data} {heads} />
{:else if activeTab === 'Stats'}
  <CardSection />
  <div class="mt-8 border-t border-gray-200 pt-8">
    <h2 class="mb-4 text-2xl font-semibold">User Content Access</h2>
  </div>
  <UserContentControls bind:selectedProvider {dataUsers} {headsUsers} onDownload={handleDownload} />
{:else}
  <div
    class="flex h-64 items-center justify-center rounded-lg border-2 border-dashed border-gray-300 bg-gray-50"
  >
    <div class="text-center">
      <div class="mb-4 text-4xl">🚧</div>
      <h3 class="mb-2 text-lg font-medium text-gray-900">Coming Soon!</h3>
      <p class="text-gray-500">{activeTab} content is under construction</p>
    </div>
  </div>
{/if} -->
