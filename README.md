<h1 align="center">AlterCove</h1>

<p align="center"><b>Draft site-wide changes in a private workspace, preview them, then publish or schedule in one step.</b></p>

<p align="center">
  <a href="https://wordpress.org/plugins/altercove/"><img src="assets/download-wporg.svg" alt="Download on WordPress.org" height="36"></a>
</p>

<p align="center">Free WordPress plugin · Version 1.0.1 · GPLv2 or later</p>

> [!NOTE]
> AlterCove is officially distributed through **WordPress.org**. Please download, install and get updates from its [WordPress.org page](https://wordpress.org/plugins/altercove/) so you always have the latest reviewed version.

## About

WordPress lets you draft a single post before publishing it. AlterCove brings a similar workflow to a wider set of site changes.

Create a private **workspace**, activate it, and keep working in wp-admin as usual. Supported changes you save are kept in the workspace instead of going live. You and anyone you share a private preview link with can see the site with those changes; everyone else keeps seeing the live site. When the workspace is ready, publish it in one step or schedule it.

AlterCove works on the same WordPress installation. It does not copy your database and it never touches orders, customers or other transactional data.

#### How to use AlterCove

**1. Create a workspace**

Go to **AlterCove > Workspaces** in the admin menu. Under “Start a new workspace”, type a name (for example “Spring homepage refresh”), keep **“Activate it now”** checked and click **Create workspace**.

While a workspace is active for you, the toolbar at the top of every screen shows **“Workspace: your workspace name”**, so you always know your changes are private.

**2. Change settings, theme options and widgets**

Work as you normally do. Save settings on the **Settings** screens, change options in **Appearance > Customize**, or edit widgets. With the workspace active, these saves are kept in the workspace instead of going live. Visitors still see the live site.

**3. Edit a post or page privately**

Open **Pages** or **Posts** and click **“Edit in workspace”** under the title (or use the **Content** tab of your workspace and search for it). AlterCove opens a private copy in the normal editor. Edit it and click **Update** or **Publish** as usual: only the private copy is saved, the live page does not change.

**4. Edit a classic menu privately**

Open the workspace’s **Menus** tab and click **“Edit in workspace”** next to a menu. A private copy opens on the Appearance > Menus screen. Rename, reorder, add or remove items there. (Block themes use the Site Editor for navigation instead; see the next step.)

**5. Edit templates and styles in the Site Editor**

For block themes, open **Appearance > Editor** while the workspace is active. Saving a template, template part, global styles or navigation menu that has already been customized on your site keeps the change in the workspace. WordPress Additional CSS is excluded from AlterCove workspaces. Deactivate the workspace before editing Additional CSS.

**6. Review your changes**

Open your workspace from **AlterCove > Workspaces**. The **Overview** tab shows your progress and every pending change. Click **“Show differences”** on any change to compare the live version with the workspace version. Use **“Remove from workspace”** to drop a change you no longer want.

**7. Preview the site**

Click **Preview site** at the top of the workspace screen to browse the front end with your changes. Only you see them. A banner at the bottom of the page lets you leave the preview at any time.

**8. Share a preview with someone else**

Open the **Preview** tab, choose how long the link should work and click **Create preview link**. Copy the link right away: for security it is shown only once. Anyone with the link can view the front end with your changes, without logging in and without any access to wp-admin. Click **Revoke** to switch a link off immediately.

**9. Resolve conflicts**

If someone changed the same setting or content on the live site after you added it to your workspace, the **Conflicts** tab shows the original, the current live and your workspace version side by side. Choose **Keep live version**, **Use workspace version**, or **Review manually** to edit it yourself. Publishing is not possible until every conflict is resolved.

**10. Publish or schedule**

Click **Publish now** at the top of the workspace screen. All changes go live together, and the workspace is marked Published. To publish later, open the **Schedule** tab, pick a date and time and click **Schedule publish**. Conflicts are checked again at that moment.

**11. Stop, pause or throw away**

- Click **Deactivate** to pause a workspace. Your changes stay saved in it, and anything you save afterwards goes to the live site as usual. Click **Activate** to continue later.
- Use **Discard workspace** on the Overview tab to delete all its private changes. The live site is not changed.

#### What a workspace can hold

- **Settings:** site title, tagline, reading, discussion and media settings, date and time formats, site icon and logo.
- **Theme customizations and widgets:** supported Customizer options and widget settings saved while the workspace is active. The Custom HTML widget is intentionally not captured.
- **Posts and pages:** “Edit in workspace” creates a private copy that you edit in the normal editor. Title, content, excerpt, order, parent, comment settings, featured image, custom fields and categories/tags are included. Developers can enable other content types.
- **Classic menus:** a private copy of the menu, edited on Appearance > Menus.
- **Site Editor:** customized templates, template parts, global styles and navigation menus saved while the workspace is active.

#### How it keeps the live site safe

- **Workspace copies can never go public.** They use an internal status that WordPress does not serve to visitors. Pressing Publish or Update on a copy only saves the copy.
- **Conflict detection.** When you add something to a workspace, AlterCove remembers the live version. Before publishing, it checks whether the live version was changed in the meantime. If it was, publishing stops and you choose: keep the live version, use the workspace version, or review it manually. Nothing is overwritten silently.
- **Best-effort rollback.** Right before each object is changed, its live state is saved. If a step fails, the steps already applied are rolled back, and settings that did not exist before are removed again. WordPress has no transaction that covers every kind of data, so rollback is best effort; side effects in other plugins or external services cannot be undone.
- **Publish lock.** Only one request can publish a workspace at a time.
- **Scheduled publishing** re-checks conflicts at publish time. If there is a conflict, nothing is published, the workspace is marked Blocked and you are emailed.
- **Secure preview links.** Links use 256-bit random keys. Only a SHA-256 hash is stored; the link is shown once. Links expire, can be revoked at any time, never give wp-admin access, and people using them cannot send forms.
- **Sensitive values** such as passwords, API keys and tokens are masked in comparisons and never written to the history.

#### What is not captured

Some changes cannot be kept privately in a safe way and are not part of an AlterCove workspace: WordPress Additional CSS, the Custom HTML widget, activating plugins or themes, site address, admin email, user and role management, media uploads, comments, deleting content, and creating new posts (new posts stay ordinary WordPress drafts). Deactivate the workspace before editing excluded code-based settings such as Additional CSS or the Custom HTML widget. WooCommerce orders, refunds, customers, sessions, coupons, products and scheduled actions are always excluded; WooCommerce settings are left live. Creating or resetting templates in the Site Editor is blocked while a workspace is active.

AlterCove does not replace a staging site for plugin updates, theme switches or code changes.

#### Compatibility notes

AlterCove includes conservative rules for Elementor, WPBakery, ACF, Yoast SEO, Rank Math, WooCommerce, Jetpack and WPForms: page-builder and SEO data stored with a post follows its workspace copy, generated caches are excluded, and Elementor caches are cleared after publishing. These rules are not a claim of full compatibility with every feature of those plugins. The Settings screen lists what applies to the plugins active on your site.

#### For developers

Filters: `altercove_capability`, `altercove_supported_options`, `altercove_excluded_options`, `altercove_supported_post_types`, `altercove_excluded_post_types`, `altercove_site_editor_post_types`, `altercove_excluded_post_meta`, `altercove_sensitive_keys`, `altercove_before_change_capture`, `altercove_publish_option_value`, `altercove_workspace_changes`, `altercove_adapters`, `altercove_schedule_grace_period`, `altercove_block_preview_writes`.

Actions: `altercove_after_change_capture`, `altercove_before_workspace_publish`, `altercove_before_apply_change`, `altercove_after_workspace_publish`, `altercove_workspace_publish_failed`, `altercove_content_published`.

Custom object types can be supported by registering a class that implements `Altercove_Adapter_Interface` through the `altercove_adapters` filter.

### Privacy

AlterCove does not track visitors, does not contact external services and does not use a CDN.

It stores the user account IDs of people who create workspaces, capture changes, create preview links and perform workspace actions, with the date of each action. The history is deleted automatically after the retention period set on the Settings screen (90 days by default). Setting values, content and preview link keys are never written to the history.

People who open a preview link receive a cookie named `altercove_preview` that holds the link key until it expires or they leave the preview. AlterCove stores no IP addresses or browser details; it only counts how often each link was used.

AlterCove adds suggested text to the privacy policy guide and supports the WordPress personal data export and erasure tools.

## Requirements

- WordPress 6.4 or higher
- Tested up to WordPress 7.1.4
- PHP 7.4 or higher

## How to install

1. In your WordPress dashboard go to **Plugins → Add New Plugin**.
2. Search for **AlterCove**.
3. Click **Install Now**, then **Activate**.

Or download it directly from **[WordPress.org](https://wordpress.org/plugins/altercove/)**.

## Support

Questions or problems? Please use the **[support forum on WordPress.org](https://wordpress.org/support/plugin/altercove/)**.

## Author

Developed by **[Muhammad Mujahid Sarfraz](https://profiles.wordpress.org/mujahidwp/)** · [All my WordPress products](https://profiles.wordpress.org/mujahidwp/) · [LinkedIn](https://www.linkedin.com/in/muhammad-mujahid-sarfraz-2631a43b6)
