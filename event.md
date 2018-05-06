---
title: Event record
---

# Event record

All events in `CepGen` are defined in the `CepGen::Event` c++ object.

## Getters

- `Event::getById(unsigned short)` and `Event::getConstById(unsigned short)`, to retrieve one single particle by its position in the event.
- `Event::getByRole(Particle::Role)` and `Event::getOneByRole(Particle::Role)`{:.language-cpp} to retrieve all, or one single particle by its role in the event.

# Particle record

## Getters

- `Particle::status`
- `Particle::role`

