# The Open Science Framework (OSF) Ecosystem

The [Open Science Framework (OSF)](https://osf.io) is a free, open-source platform maintained by the [Center for Open Science (COS)](https://www.cos.io) that supports researchers in managing, sharing, and preserving their work. OSF is built with several interconnected services that enable seamless collaboration, file management, and integrations with external tools.

---

## OSF Core Platform ([osf.io](https://github.com/CenterForOpenScience/osf.io))

The backbone of OSF, this repository manages study designs, datasets, manuscripts, and more. The backend is primarily built with Python using Django. It integrates PostgreSQL, Redis, and RabbitMQ for data management and task processing.  
➡️ **[Learn how to contribute to OSF](https://github.com/CenterForOpenScience/osf.io)**

---

## OSF Frontend ([Angular-based Web Interface](https://github.com/CenterForOpenScience/osf-angular))

The current user interface for OSF is being transitioned from Ember.js to AngularJS to provide better performance, maintainability, and a more modular architecture. The frontend communicates with the OSF RESTful API to deliver a responsive and intuitive user experience.  
➡️ **[Learn how to contribute to the OSF Angular frontend](https://github.com/CenterForOpenScience/osf-angular)**

---

## WaterButler ([File Management API](https://github.com/CenterForOpenScience/waterbutler))

A Python-based service that enables file storage interactions across various external services (e.g., Google Drive, Dropbox) through a unified API.  
➡️ **[Learn how to contribute to WaterButler](https://github.com/CenterForOpenScience/waterbutler)**

---

## OSF Add-ons ([GravyValet](https://github.com/CenterForOpenScience/gravyvalet))

A microservice that manages integrations between OSF and external services like cloud storage and citation tools. It defines a shared API for enabling these features within OSF.  
➡️ **[Learn how to contribute to GravyValet](https://github.com/CenterForOpenScience/gravyvalet)**

---

## How OSF Components Work Together

OSF’s architecture consists of multiple services that communicate through APIs to ensure smooth data management, file handling, and user interactions.

- **User Interactions** → The user interface (`ember-osf-web` / `AngularJS`) communicates with OSF’s core backend via API calls.  
- **File Management** → WaterButler enables file transfers by connecting OSF with external storage services.  
- **Add-ons & Integrations** → GravyValet manages authentication and API calls for external services, working alongside WaterButler for file operations.  
- **Data Storage & Processing** → The OSF Core Platform handles study data, metadata, and user-generated content with PostgreSQL and Redis.

---

✅ Maintained by [Center for Open Science](https://www.cos.io)  
📢 Contributions welcome! Check out the linked repositories above to get started.
