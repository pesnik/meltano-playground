# Meltano Playground

A hands-on laboratory for mastering Meltano - the open-source DataOps framework that brings together industry-standard data tools and best practices.

## 🎯 Purpose

This playground helps you:
- Master Meltano's core concepts through practical examples
- Experiment with different extractors and loaders
- Learn pipeline orchestration patterns
- Understand Meltano's plugin ecosystem
- Practice DataOps workflows with Meltano

## 📂 Project Structure

```
meltano-playground/
├── basics/
│   ├── 01-installation/           # Getting started with Meltano
│   ├── 02-project-structure/      # Understanding project organization
│   ├── 03-tap-configuration/      # Configuring data sources
│   └── 04-target-setup/          # Setting up data destinations
├── pipelines/
│   ├── 01-simple-pipeline/       # Basic EL pipeline
│   ├── 02-scheduled-pipeline/    # Adding scheduling
│   ├── 03-transformed-pipeline/  # Including transformations
│   └── 04-complex-pipeline/      # Advanced pipeline patterns
├── plugins/
│   ├── custom-extractor/         # Building custom extractors
│   ├── custom-loader/            # Creating custom loaders
│   └── extensions/               # Meltano extensions
└── advanced/
    ├── orchestration/            # Advanced orchestration
    ├── testing/                  # Pipeline testing
    └── monitoring/               # Pipeline monitoring
```

## 🎓 Learning Modules

### 1. Meltano Basics
- Installing and configuring Meltano
- Understanding project structure
- Managing environment variables
- Working with meltano.yml
- Using the CLI effectively

### 2. Data Pipeline Fundamentals
- Setting up Singer taps
- Configuring targets
- Managing state files
- Handling incremental replication
- Implementing error handling

### 3. Advanced Pipeline Features
- Scheduling jobs with Airflow
- Adding dbt transformations
- Implementing data tests
- Setting up monitoring
- Managing pipeline metadata

### 4. Custom Development
- Creating custom extractors
- Building custom loaders
- Developing Meltano extensions
- Writing pipeline tests
- Building monitoring solutions

## 💻 Hands-on Examples

### Basic Pipeline
```bash
# Initialize a new Meltano project
meltano init demo-pipeline

# Add a tap (source)
meltano add extractor tap-postgres

# Add a target (destination)
meltano add loader target-snowflake

# Run the pipeline
meltano run tap-postgres target-snowflake
```

### Scheduled Pipeline
```yaml
# meltano.yml
schedules:
- name: daily-load
  extractor: tap-postgres
  loader: target-snowflake
  interval: '@daily'
  start_date: 2024-01-01
```

### Transform Pipeline
```yaml
# meltano.yml
transforms:
- name: transform-sales
  pip_url: dbt-core
  vars:
    schema: raw
```

## 🔧 Common Patterns

### Error Handling
```yaml
# meltano.yml
jobs:
  my-pipeline:
    tasks:
    - tap-postgres target-snowflake
    on_failure:
      notify: true
```

### State Management
```bash
# Using state files
meltano run tap-postgres target-snowflake --state-id=incremental
```

### Custom Configuration
```yaml
# custom-config.yml
config:
  start_date: '2024-01-01'
  batch_size: 10000
```

## 🚀 Getting Started

1. Clone this repository:
```bash
git clone https://github.com/pesnik/meltano-playground.git
cd meltano-playground
```

2. Install Meltano:
```bash
pip install meltano
```

3. Navigate to a module:
```bash
cd basics/01-installation
```

4. Follow the README in each module for specific instructions

## 📚 Resources

### Official Documentation
- [Meltano Documentation](https://docs.meltano.com/)
- [Singer Spec](https://hub.meltano.com/singer/spec)
- [Meltano SDK](https://sdk.meltano.com/)

### Community Resources
- [Meltano Hub](https://hub.meltano.com/)
- [Meltano Slack](https://meltano.com/slack)
- [Meltano Blog](https://meltano.com/blog)

### Related Projects
- [being-dataops-engineer](../being-dataops-engineer)
- [singer-playground](../singer-playground)
- [dbt-playground](../dbt-playground)

## 🤝 Contributing

Contributions welcome! Add new examples, improve documentation, or fix bugs:

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## ⚖️ License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🎯 Next Steps

After completing the modules in this playground:
1. Build a production pipeline using Meltano
2. Contribute to the Meltano ecosystem
3. Join the Meltano community
4. Share your learnings and help others
