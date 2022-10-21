# Welcome to project Boring-Wozniak

## Table of contents
1. [Table of contents](#table-of-contents)
2. [Introduction](#Introduction)
3. [Authors](#Authors)
4. [The case study](#the-case-study)
5. [The data](#the-data)
5. [Why is Wozniak boring? ](#why-is-wozniak-boring)

## Introduction
This repository is the authors' implementation for the projects developed during the [Database 2](https://en.didattica.unipd.it/off/2021/LM/IN/IN2547/004PD/INQ0091645/N0) course. Taught at the [Department of Information Engineering](https://www.unipd.it/en/dei) at the [University of Padova](https://www.unipd.it/en/)

The goal of the projects is to boost soft skills like teamwork and collaboration. Project deadlines are aligned with the schedule and contents of the lectures so that students can immediately apply the learned concepts to a case study of their own interests.

## Authors
* [Aliia Sultanova](mailto:aliia.sultanova@studenti.unipd.it)
* [Michele Canale](mailto:michele.canale.1@studenti.unipd.it)
* [Odai Mohammad](mailto:odai.mohammad@studenti.unipd.it)
* [Yongxiang Ji](mailto:yongxiang.ji@studenti.unipd.it)

## The case study
The authors' case study is modeling the transportation network in Italy. The data used is obtained from OpenStreetMap. This data can be obtained from Geofabrik's free download [server](https://download.geofabrik.de/index.html).

## The data
The modeled data can be obtained from Geofabrik's free download [server](https://download.geofabrik.de/index.html). More specifically, the data for Italy's transportation network can be downloaded from [this link](https://download.geofabrik.de/europe/italy-latest.osm.pbf).

## Why is Wozniak boring? 

When a container is created using Docker, Docker provides a way to name the container using the `--name <container_name>` flag. However, if no name is provided by the user while creating/running a Docker container, Docker automatically assigns the container a name.

Digging into the source code of Docker on GitHub, we come across the algorithm used to generate the names. The code is written in the file [names-generator_test.go](https://github.com/docker/docker-ce/blob/master/components/engine/pkg/namesgenerator/names-generator.go)

At line 841 we have a function GetRandomName that generates the name of the docker container:

    func GetRandomName(retry int) string {
    begin:
        name := left[rand.Intn(len(left))] + "_" + right[rand.Intn(len(right))] //nolint:gosec // G404: Use of weak random number generator (math/rand instead of crypto/rand)
        if name == "boring_wozniak" /* Steve Wozniak is not boring */ {
            goto begin
        }

        if retry > 0 {
            name += strconv.Itoa(rand.Intn(10)) //nolint:gosec // G404: Use of weak random number generator (math/rand instead of crypto/rand)
        }
        return name
    }

Looking at this snippet of the function: 

    if name == "boring_wozniak" /* Steve Wozniak is not boring */ {
            goto begin
    }

Our friends at Docker think that Steve Wozniak is not boring. We agree, but we couldn't resist throwing an inside joke into our project.
