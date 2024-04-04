![github](https://github.com/Devfront-end/Devfront-end/blob/main/github_banner.png)

### Hi there 👋, my name is Jules

#### I am a Front-end developer with Software Testing skills

From pixels to performance, I bridge the gap: Front-end dev & QA in one.

- 🌱 I’m currently learning Python/Django and Swift 
- ❤️  Innovative technologies such as AI
- 👯 I’m looking to collaborate on creating web and mobile applications
- 🖥️ I always love to learn, discover new things
- ⚡ Fun fact: Writing
- [<img src='https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/hashnode.svg' alt='dev' height='40'>](https://jules.hashnode.dev/)  My blog

[![Devfront-end's GitHub stats-Light](https://github-readme-stats.vercel.app/api?username=Devfront-end&show_icons=true&theme=default#gh-light-mode-only)](https://github.com/Devfront-end/github-readme-stats#gh-light-mode-only)

[![Devfront-end's GitHub stats-Dark](https://github-readme-stats.vercel.app/api?username=Devfront-end&show_icons=true&theme=dark#gh-dark-mode-only)](https://github.com/Devfront-end/github-readme-stats#gh-dark-mode-only)

```swift
import SwiftUI

struct JobApplication: Identifiable {
    let id = UUID()
    var companyName: String
    var position: String
    var applicationDate: Date
}

struct ContentView: View {
    @State private var jobApplications = [JobApplication]()
    @State private var newCompanyName: String = ""
    @State private var newPosition: String = ""
    @State private var newApplicationDate: Date = Date()

    var body: some View {
        NavigationView {
            VStack {
                Form {
                    Section(header: Text("Add New Application")) {
                        TextField("Company Name", text: $newCompanyName)
                        TextField("Position", text: $newPosition)
                        DatePicker("Application Date", selection: $newApplicationDate, displayedComponents: .date)
                        HStack {
                            Button("Add Job Application") {
                                let newApplication = JobApplication(companyName: newCompanyName, position: newPosition, applicationDate: newApplicationDate)
                                jobApplications.append(newApplication)
                                resetForm()
                            }
                            .disabled(newCompanyName.isEmpty || newPosition.isEmpty)
                            
                            Button("Reset") {
                                resetForm()
                            }
                        }
                    }
                }
                
                List {
                    ForEach(jobApplications) { application in
                        VStack(alignment: .leading) {
                            Text(application.companyName).font(.headline)
                            Text(application.position)
                            Text("Applied on \(application.applicationDate, formatter: itemFormatter)")
                        }
                    }
                    .onDelete(perform: deleteJobApplication)
                }
            }
            .navigationTitle("Job Application Tracker")
            .toolbar {
                ToolbarItem(placement: .navigationBarTrailing) {
                    EditButton()
                }
                ToolbarItem(placement: .navigationBarLeading) {
                    Button("Delete All") {
                        jobApplications.removeAll()
                    }
                }
            }
        }
    }

    private func resetForm() {
        newCompanyName = ""
        newPosition = ""
        newApplicationDate = Date()
    }

    private func deleteJobApplication(at offsets: IndexSet) {
        jobApplications.remove(atOffsets: offsets)
    }
}

private let itemFormatter: DateFormatter = {
    let formatter = DateFormatter()
    formatter.dateStyle = .long
    return formatter
}()

struct ContentView_Previews: PreviewProvider {
    static var previews: some View {
        ContentView()
    }
}


<!--
**Devfront-end/Devfront-end** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.


-->


